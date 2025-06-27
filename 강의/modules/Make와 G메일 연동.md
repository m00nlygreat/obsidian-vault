## Make와 G메일 연동

- G메일과 같은 개인정보에 민감한 서비스에 대한 API 사용은 까다로워서, 회사 단위의 Google Workspace(전 G Suites)를 구독하지 않는 한 기본적으로 Make와의 연동되지 않음
	- 전사적으로 G메일을 사용하고 이메일 주소가 gmail.com 이 아닌 것
- 따라서 구글 클라우드 플랫폼(이하 GCP)에서 프로젝트를 등록하고, API의 허용 범위와 사용 신청
	- 커스텀 Client ID와 Client Secret을 사용하는 방법으로 oAuth 로그인을 해야 함
- [G메일과 Make 연동하기.pdf 참고](https://drive.google.com/file/d/19nuEHqB_igGDb35ujPkOmrUScNJ01fX7/view?usp=sharing)
	- [Make documentation](https://www.make.com/en/help/app/gmail)

![](../attachments/make-gmail_inte.png)

