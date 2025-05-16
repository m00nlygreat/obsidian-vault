[https://mc-questing-mod-localizer.streamlit.app/](https://mc-questing-mod-localizer.streamlit.app/)

리소스팩은 아래와 같이 구성

- pack.mcmeta
- pack.png
- assets
	- minecraft
		- ko_kr.json
		- en_us.json

`minecraft` 네임스페이스를 사용하는데, 키만 맞으면 잘 불러오는 모양이다

서버에서는 /config/ftbquests/quests/chapters 만 덮어씌우면 된다.
