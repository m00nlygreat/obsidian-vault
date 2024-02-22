요즘 레노버 제품이 핫한데.. 구글 플레이 관련해서 다들 고민이 많으신 것 같네요.

특히 P11 같이 글로벌 롬이 없는 중국 내수롬 제품들이 구글 플레이 인앱 결제가 안되는 등의 불편함이 있는 것 같습니다.

사실 안드로이드가 지역별 정책을 가지고 있지만 내수롬들이 직접 구글을 지원하게 되면 문제가 여러가지 생기다보니..

우회적으로 자체 스토어 등을 이용해서 구글 플레이 기본 기능만 사용하게 해주지, 인앱 결재 등은 지원을 안하려고 합니다.

....하지만 안드로이드는 기본적으로 인앱 결제 가능한 환경만 만들어주면 지역에 따라 작동을 하는 구조이기 때문에

내수롬에 없는 서비스 프레임워크 등의 요소만 설치해주면 얼마든지 인앱 결제 데이터를 불러올 수 있고 결제도 가능합니다.

반대로 이걸 하겠다고 우회 방법이나 VPN 등을 쓰면.. 계정 밴 당할 확률이 매우 높아집니다.

물론 이 방법으로 기존 한국에서 사용하던 계정을 Legion Y700에 사용한다고해서 100%  안전한 것은 아니지만 적어도 정식 구글 서비스를 이용하는 것이기 때문에 밴당할 확률 자체는 낮다고 생각합니다.

심플하게 아래 과정을 수행하면 최신 구글 플레이 및 구글 서비스 대부분을 Legion Y700에서도 사용하실 수 있습니다.

\[ 주의 사항 \]

 - 이 작업 후 구글 계정의 사용에 제한이 걸린다면 구글과 상의해서 푸셔야 합니다. (정책적으로는 문제가 없습니다만..)

 - Legion Y700 펌웨어의 보안 패치 날짜와 연관 있는 작업이며, 이 글을 작성하는 시점의 최신 펌웨어인 ZUI 14.0.231 ST 기준 정상 작동하는 방법입니다. (이하 펌웨어에서는 정상 동작이 안될 수 있습니다.)

1\. 사전 준비

 - APK Mirror에서 아래 항목을 다운로드 합니다. (모두 APK로 다운 받아야 합니다.)

 - Carrier Service ([링크](https://www.apkmirror.com/apk/google-inc/carrier-services-2/carrier-services-2-carrierservices-android_20230104_00_rc00-phone-release/carrier-services-carrierservices-android_20230104_00_rc00-phone-android-apk-download/?redirected=download_invalid_nonce "실제 링크
<주소>
https://www.apkmirror.com/apk/google-inc/carrier-services-2/carrier-services-2-carrierservices-android_20230104_00_rc00-phone-release/carrier-services-carrierservices-android_20230104_00_rc00-phone-android-apk-download/
<파라미터>
redirected=download_invalid_nonce")https://www.apkmirror.com/apk/google-inc/carrier-services-2/carrier-services-2-carrierservices-android\_20230104\_00\_rc00-phone-release/carrier-services-carrierservices-android\_20230104\_00\_rc00-phone-android-apk-download/?redirected=download\_invalid\_nonce)

 - Google Services Framework ([링크](https://www.apkmirror.com/apk/google-inc/google-services-framework/google-services-framework-12-release/google-services-framework-12-android-apk-download/?redirected=download_invalid_nonce "실제 링크
<주소>
https://www.apkmirror.com/apk/google-inc/google-services-framework/google-services-framework-12-release/google-services-framework-12-android-apk-download/
<파라미터>
redirected=download_invalid_nonce")https://www.apkmirror.com/apk/google-inc/google-services-framework/google-services-framework-12-release/google-services-framework-12-android-apk-download/?redirected=download\_invalid\_nonce)

 - Google Play Services ([링크](https://www.apkmirror.com/apk/google-inc/google-play-services/google-play-services-22-49-15-release/google-play-services-22-49-15-150406-499306216-android-apk-download/?redirected=download_invalid_nonce "실제 링크
<주소>
https://www.apkmirror.com/apk/google-inc/google-play-services/google-play-services-22-49-15-release/google-play-services-22-49-15-150406-499306216-android-apk-download/
<파라미터>
redirected=download_invalid_nonce")https://www.apkmirror.com/apk/google-inc/google-play-services/google-play-services-22-49-15-release/google-play-services-22-49-15-150406-499306216-android-apk-download/?redirected=download\_invalid\_nonce)

 - Google Play ([링크](https://www.apkmirror.com/apk/google-inc/google-play-store/google-play-store-33-9-15-release/google-play-store-33-9-15-21-0-pr-498467920-3-android-apk-download/?redirected=download_invalid_nonce "실제 링크
<주소>
https://www.apkmirror.com/apk/google-inc/google-play-store/google-play-store-33-9-15-release/google-play-store-33-9-15-21-0-pr-498467920-3-android-apk-download/
<파라미터>
redirected=download_invalid_nonce")https://www.apkmirror.com/apk/google-inc/google-play-store/google-play-store-33-9-15-release/google-play-store-33-9-15-21-0-pr-498467920-3-android-apk-download/?redirected=download\_invalid\_nonce)

2\. 앱 설정 변경

 - 기존에 Lenovo Legion Y700의 기본 스토어에서 설치한 Google Play를 초기 버전으로 되돌립니다.

   (Settings →  App Magenent → Google Play 스토어 → Force Stop 선택  →  오른쪽 위 ... 선택 후 Uninstall Update 선택)

 - 구글 서비스가 비활성화 되어 있는 경우 활성화 합니다.

  (Settings →  App Magenent → 오른쪽 위 ... 선택 후 Google Basic Services 선택 →  활성화)

3\. 앱 설치

 - 다운 받은 APK를 아래 순서대로 설치해주세요. (이미 있는 앱인 경우 그냥 업데이트 처리하시면 됩니다. 왠만하면 덮어서 설치됩니다.)

 - Carrier Service →  Google Services Framework →  Google Play Services →  Google Play

 - 설치 완료 후 실행하지 않고 재부팅합니다.

4\. Google 계정 연동

 - Google Play를 실행해서 로그인합니다.

 - 로그인 후 Google Service 활성을 위해서 'Google' 앱을 설치해주세요. (이 앱 설치로 추가적인 서비스 항목이 활성화 됩니다.)

  (게임을 주로하신다면 'Google Play 게임'도 설치해주세요.)

 - 인앱 결제 항목을 포함하는 앱을 실행해서 인앱 결제 목록(원화로 결제되는 상품)이 정상적으로 호출되면 결제도 정상적으로 가능한 환경이 됩니다.

  (결제 프로세스가 불가능한 경우에는 원화 결제 항목이 출력되지 않고 목록 출력 전에 에러가 발생하도록 되어 있습니다.)

위 과정만 수행해주시면 인앱결제 및 구글 플레이 사용에 대한 대부분의 제약이 사라질 겁니다.

그리고 Legion Y700이 게이밍 태블릿이다보니.. Sercurity 앱에서 백그라운드 서비스를 아주 잘 죽이기로 유명한데 이렇게 설치한 구글 서비스들을 기본 앱으로 지정해두어도 종료시키는 경우가 있습니다. 

이런 경우에 인앱 결제 포함된 앱(게임 등)을 실행하면 원화 결제 항목이 안나오고 경고 팝업이 출력될 수 있는데, 아래 방법으로 해결할 수 있습니다.

\- 멀티태스킹 화면에서 구글 플레이 앱 아이콘 터치 -> Lock 선택

\- 또는 Settings → Battery → 하단 배터리 사용 내역에서 Google Play 스토어 선택 →  Unrestricted 선택

위와 같이 조치하시면 기본적인 Google 서비스가 램에서 내려가지 않아서 해당 현상이 완화됩니다. (둘 중 하나만 하셔도 됩니다.)

그래도 아주 가끔 스토어 로그인을 하라는 경고가 나올 경우가 있는데 이럴 때도 구글 플레이를 한번 실행해주시면 해결될 겁니다.

마지막으로 사족이긴 한데, 위 방법으로 대부분의 중국 내수롬의 구글 플레이를 활성화할 수 있습니다.

주의 사항은 위 패키지 4종이 반드시 설치되어야 한다는 전제가 있는데 이 패키지를 고르시는 기준은 해당 기기의 안드로이드 버전 + 보안 패치 날짜를 참고하면 됩니다.

안드로이드 버전 + 보안 패치 날짜 이후 배포된 APK를 설치하면 대부분 활성화가 되실겁니다. :)