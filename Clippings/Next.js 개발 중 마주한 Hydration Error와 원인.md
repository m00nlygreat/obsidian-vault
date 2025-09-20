---
title: "Next.js 개발 중 마주한 Hydration Error와 원인"
source: "https://techblog.gccompany.co.kr/next-js-%EA%B0%9C%EB%B0%9C-%EC%A4%91-%EB%A7%88%EC%A3%BC%ED%95%9C-hydration-error%EC%99%80-%EC%9B%90%EC%9D%B8-a439ee2345aa"
author:
  - "[[Henby]]"
published: 2025-08-07
created: 2025-09-21
description: "Next.js 개발 중 마주한 Hydration Error와 원인 안녕하세요. 서비스웹개발팀의 헨비입니다.  이번 패키지 여행 상품 추가 프로젝트를 진행하면서, React …"
tags:
  - "clippings"
---
GC Company Tech Blog

안녕하세요. 서비스웹개발팀의 헨비입니다.  
이번 패키지 여행 상품 추가 프로젝트를 진행하면서, React, Next.js를 개발 했던 **Front-End 개발자** 라면 익숙할 Next.js의 SSR Hydration Error를 다시 한번 겪게 되었습니다. 이번에는 단순 해결을 넘어, 원인과 동작 원리를 깊이 공부해 본 경험을 정리해보려 합니다.

## 갑자기 발생한 “Hydration Error”

1차 개발이 완료 된 후 Feature를 QA를 위해 Dev Server에 첫 배포 후 갑자기 Hydration Error가 발생했습니다.

## Hydration Error가 무엇일까?

**Hydration Error** 는 **Next.js** 나 **React SSR** 환경에서, 클라이언트가 서버에서 렌더(render)된 **HTML** 을 재사용(hydrate)할 때 서버와 클라이언트의 렌더링 결과가 다를 경우 발생하는 오류를 말합니다.

![](https://miro.medium.com/v2/resize:fit:640/format:webp/0*VMsEBR-KDlKDKKbo.png)

출처: https://dev.to/iamdevmarcos/react-hydration-explained-3lk0

즉, 페이지의 HTML을 서버에서 미리 렌더링해 사용자에게 빠르게 보여준 뒤, 클라이언트에서 **React** 가 이를 T **akeover** 하는 과정에서 내용이 다르면, **React** 는 이를 **일관성 오류(inconsistency)** 로 간주하고 에러를 발생시킵니다.

> **CSR(Client Side Rendering)** 만 사용하는 **SPA** 에서는 이런 문제가 드물지만, **Next.js** 처럼 **SSR(Server Side Rendering)** 과 **CSR** 을 혼합해 사용하는 경우, 서버에서 렌더링된 HTML과 클라이언트 렌더링 결과가 다르면 예상치 못한 UI 깨짐, 깜빡임(flicker), 기능 오류 등 심각한 사용자 경험 저하로 이어질 수 있습니다.

비동기 처리 데이터, 시간, 랜덤 값, 브라우저 API(window, navigator) 등을 서버 렌더에서 그대로 사용할 경우, 서버와 클라이언트의 실행 환경 차이로 인해 **hydration mismatch** 가 쉽게 발생합니다.

## 원인을 찾아 떠나는 여행

2달간 3명의 인원이 만든 대형 코드가 Local에서는 빌드와 테스트까지 모두 잘 되었지만, d **ev** 환경에서 갑자기 에러가 발생하니 당황할 수밖에 없었습니다. **더군다나 다음 날부터 QA가 진행될 예정이었으니 말이죠.**

> 하지만 개발자라면 이런 에러를 마주했을 때 오히려 침착하게 문제를 디테일하게 파악하고, 이를 통해 더 성장할 수 있어야 합니다.

1. local serve는 잘 되었다.
2. local build + pm2도 잘 되었다.
3. dev 환경 변수로 local serve, build도 잘 되었다.
4. dev 서버에 배포만 하면 hydration error가 발생했다.
5. dev 서버의 기존 코드에서는 문제가 없었다.

**결국 원인은 dev 서버에서 새로운 코드가 에러를 만들어내고 있다는 것이었습니다.**

## Hydration Error 발생 시 행동 지침

### 1\. SSR과 CSR에서 값이 달라지는 코드 패턴 찾기

서버는 브라우저 API(window, document, localStorage 등)를 모릅니다.

- useEffect나 useLayoutEffect **밖에서** window, document, localStorage 등을 사용하고 있는지 확인
- 서버에서 계산한 값과 클라이언트에서 계산한 값이 다르면 Hydration Mismatch가 발생합니다.

**잘못된 예시 (SSR에서 에러)** ❌

```c
// SSR에서 실행시 ❌
const [userAgent] = useState(() => window.navigator.userAgent);
```

✅ **권장 예시**

```c
// CSR에서 ✅
const [userAgent, setUserAgent] = useState('');

useEffect(() => {
  setUserAgent(window.navigator.userAgent);
}, []);

// SSR에서 ✅ (getServerSideProps 사용)
export async function getServerSideProps(context) {
  const userAgent = context.req.headers['user-agent'] || '';
  return {
    props: {
      userAgent,
    },
  };
}
```

### 2\. 날짜, 시간, 랜덤 값 사용 여부 점검

new Date(), Math.random() 등은 SSR 시점과 Hydration 시점의 값이 달라질 수 있습니다. 이로 인해 mismatch가 발생합니다.

**예시**

- Random ID 생성
- 현재 시간 출력
- dayjs(), new Date()를 useMemo, useState 초기값으로 직접 할당

✅ **해결**

- **Client-side** 에서만 계산하도록 **useEffect** 사용
- **SSR** 에서 계산 필요 시 **getServerSideProps** 로 전달

### 3\. 상태 관리(Store) 초기값 일관성 확인

Recoil등 클라이언트 상태 관리의 초기값이 SSR과 CSR에서 다르게 세팅될 수 있습니다

예) 쿠키, localStorage 기반 유저 데이터가 SSR에서는 undefined, CSR에서는 값이 있을 수 있습니다.

✅ **해결**

- SSR safe 기본값 설정
- useEffect에서 브라우저 API 접근 후 setState
- 필요 시 dynamic import + ssr: false로 hydration mismatch 방지

### 4\. Hydration 대체 전략 고려

특정 컴포넌트는 SSR하지 않고 CSR에서만 렌더링해도 무방하다면

```c
import dynamic from 'next/dynamic';

const NoSSRComponent = dynamic(() => import('./NoSSRComponent'), { ssr: false });
```

또는 Skeleton UI, Suspense 등을 사용해 초기 **mismatch** 를 방지할 수 있습니다.

## 우리 의 원인은?

우리 조직에는 예전부터 **dayjs** 를 이용한 `date.ts` 유틸 파일이 두 개 존재하고 있었습니다.

차근차근 코드를 확인하던 중, 최근 패키지 개발 과정에서 **dayjs** 를 활용한 **date formatter** 함수를 몇 가지 새로 만들었는데,  
혹시 서버의 날짜와 클라이언트의 날짜가 달라 문제가 생겼나? 라는 의문이 들어 코드를 살펴보았습니다.

```c
import dayjs from 'dayjs';
import utc from 'dayjs/plugin/utc';
import timezone from 'dayjs/plugin/timezone';

dayjs.extend(utc);
dayjs.extend(timezone);

/**
 * string 날짜를 Y. M. D (dd)로 변경하는 함수
 * @param time 20200601
 * @returns {string} 25.6.1 (수)
 */
const getFormatCompactDateWithDay = (date: string | number): string => {
  if (!date) return '';
  const parsedDate = dayjs(date.toString(), 'YYYYMMDD');
  return parsedDate.format('YY.M.D(dd)');
};
```

문제가 무엇인지 파악되셨나요?

맞습니다. **서버의 기본 언어(locale)는** `**en**` **이고, 클라이언트의 설정 언어는** `**ko**` **였습니다.**

기존 코드에는 요일을 불러오는 로직이 없었고, 더군다나 다른 `**date.ts**` 파일은 locale 설정이 되어 있었기 때문에, 문제의 원인을 파악하기가 더욱 어려웠습니다.

## 🧐 왜 이런 문제가 발생했을까?

Next.js의 SSR(Server Side Rendering)은 Node.js 환경에서 렌더링되기 때문에, 기본적으로 서버는 **‘en-US’** 와 같은 locale을 사용합니다. 반면, 브라우저(클라이언트)는 사용자가 설정한 언어 환경(한국어 ko-KR)을 사용합니다.

즉, 같은 dayjs 코드라도:

- **서버 사이드:** 영어 요일로 포맷 (예: Wed)
- **클라이언트 사이드:** 한글 요일로 포맷 (예: 수)

이렇게 다른 문자열이 생성되어, Hydration 시점에 React가 두 결과의 차이를 감지하고 **Hydration Error를 발생** 시킨 것입니다.

## 💡 이번 경험을 통해 다시 배운 점

1. **날짜/시간/locale 기반 포맷팅은 SSR Safe하지 않을 수 있다.**
- 클라이언트 환경에서만 필요한 포맷이라면 `useEffect` 에서 처리하거나,  
	서버에서 처리해야 한다면 서버의 locale과 timezone을 **명시적으로 지정** 해야 합니다.

2\. **dayjs는 locale 설정이 글로벌하게 적용됩니다.**

- 따라서 SSR 진입점(server.js 등)에서 한국어 locale을 먼저 설정하거나,  
	서버 전용 formatter를 만들어주는 것이 안전합니다.

3\. **Hydration** **Error** 는 보통 **데이터 불일치** 로 발생한다.

- 랜덤값, 날짜/시간, 브라우저 API(window, navigator 등)를 사용하는 코드 모두 점검 대상입니다.

## ✨ 끝으로

이번 문제를 해결하면서 다시 한번 **SSR과 Hydration의 본질** 을 깊게 이해할 수 있었습니다.  
자주 겪는 에러일수록 ‘왜 이런 문제가 생기는가?’를 파고드는 과정에서 개발자로서 한층 성장하게 되는 것 같습니다.

끝까지 읽어주셔서 감사합니다.

이 글이 비슷한 문제를 겪는 분들에게 작은 도움이 되길 바랍니다.

## More from Henby and 여기어때 기술블로그

## Recommended from Medium

[

See more recommendations

](https://medium.com/?source=post_page---read_next_recirc--a439ee2345aa---------------------------------------)