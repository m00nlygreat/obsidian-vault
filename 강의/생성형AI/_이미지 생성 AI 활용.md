## 이미지 생성형 AI

::: {.columns}
::: {.column}

### 종류

- [Stable Diffusion](https://stability.ai/): Stability AI의 오픈소스 이미지 생성 모델
- [Flux.1](https://blackforestlabs.ai/): Stability AI로부터 나온 인력들이 만든 Black Forest Labs가 만든 오픈소스 모델
- [MidJourney](https://www.midjourney.com/): Diffusion 기반의 이미지 생성 모델/서비스
- [Dall-E](https://openai.com/index/dall-e-3/): ChatGPT에 통합(Integrated)된 이미지 모델. 텍스트 이해가 뛰어남 
- [Imagen](https://deepmind.google/technologies/imagen-3/): 구글 Deepmind의 이미지 생성 모델


:::
::: {.column}

### 응용 서비스

- [Leonardo.ai](https://leonardo.ai/): 다양한 이미지 생성 모델을 제공하는 웹 기반 이미지 생성 서비스
- [Replicate](https://replicate.com/): LORA 등의 개발자 수준 기능을 지원하는 GPU 대여 이미지 생성 서비스
- [Whisk](https://labs.google/fx/tools/whisk): Imagen 모델을 활용, 전경, 배경, 스타일을 이미지로 입력받아 이미지를 생성하는 UI가 특징
- [Nordy.ai](https://nordy.ai/): 국산 Comfy UI 웹 서비스

:::
:::

## txt2img

### 텍스트 프롬프트로 이미지 생성하기

- 쉼표로 구분한 키워드를 여러 개 작성하는 것이 보통
	- DALL-E를 제외한 이미지 생성 모델들은 텍스트 해석이 약하기 때문에 복잡한 문장을 받아들이기 어렵다.
- 전경, 배경, 피사체, 스타일로 구분해 프롬프트 쓰기
- GPTs 사용하기

## img2txt

- Image 2 Text 사용해서 이미지 설명하고 프롬프트에 참고하기
- 언어모델의 멀티모달 기능을 활용 (GPT4-Vision)
- 미드저니에서는 `/describe`를 사용

## style reference

- 스타일 레퍼런스 사용하기

## 고급 편집 기술

- InPainting
- OutPainting(Uncrop)

![](D:/vault/강의/생성형AI/attachments/genAI-in_out_paint.png)

# 이미지 생성 프롬프트

# 일반적인 키워드

## 정서

![](D:/vault/강의/생성형AI/attachments/genAI-emotional_prompts.png)

## 구조와 규모

![](D:/vault/강의/생성형AI/attachments/genAI-size_and_structure.png)

## 느낌, 바이브

![](D:/vault/강의/생성형AI/attachments/genAI-looks_vibes_punks_waves.png)

# 실사

## 실사 사진을 만들기 위한 프롬프트

::: {.columns}
::: {.column}

- 사진이 어떻게 구성되었나?
- 정서적인 느낌은 어떠한가?
- 어떤 앵글로 얼마나 가까이에서 찍혔나?
- 피사계 심도(Depth of field)는 어느정도?
- 빛은 어느방향에서 얼마나 와서 피사체에 얼마나 부딪히는가?
- 자연광인가 인공광인가? 빛의 색은? 하루 중 언제 찍혔나?

:::
::: {.column}

- 어떤 카메라, 어떤 렌즈를 사용했나? 접사/망원/광각?
- 스튜디오? 아니면 세상의 어딘가. 어디에서 찍혔나?
- 디지털/아날로그 어떤 카메라를 사용했나?
- 어떤 시대의 사진인가?
- 사진은 언제 어떤 상황에 출판되거나 사용되었나?

:::
:::

---

## 실사 사진을 만들기 위한 프롬프트

![](D:/vault/강의/생성형AI/attachments/genAI-photography_prompt.png)

## 피사체와의 거리

![](D:/vault/강의/생성형AI/attachments/genAI-angles_proximity.png)

## 카메라의 위치

![](D:/vault/강의/생성형AI/attachments/genAI-angles_position.png)

## 카메라 설정 / 렌즈

![](D:/vault/강의/생성형AI/attachments/genAI-camera_setting_lens.png)

## 자연광

![](D:/vault/강의/생성형AI/attachments/genAI-lighting_natural.png)

## 인공광

![](D:/vault/강의/생성형AI/attachments/genAI-lighting_artificial.png)

## 영화적 연출

![](D:/vault/강의/생성형AI/attachments/genAI-creative_photo.png)

---

## 영화적 연출

![](D:/vault/강의/생성형AI/attachments/genAI-creative_photo2.png)

## 레퍼런스: TV쇼 / 영화

![](D:/vault/강의/생성형AI/attachments/genAI-film_tv_prompts.png)

## 레퍼런스: 사진 관련 업계 

![](D:/vault/강의/생성형AI/attachments/genAI-photo_genres_usage.png)

## 레퍼런스: 유명 사진작가

![](D:/vault/강의/생성형AI/attachments/genAI-photographer.png)

# 그림

## 흑백, 아날로그

![](D:/vault/강의/생성형AI/attachments/genAI-monochrome.png)

## 컬러, 아날로그

![](D:/vault/강의/생성형AI/attachments/genAI-colour_analog.png)

## 디지털

![](D:/vault/강의/생성형AI/attachments/genAI-digital_illustration.png)

## 교육 / 정보전달

![](D:/vault/강의/생성형AI/attachments/genAI-instructional_illustration.png)

## 3D / 텍스처

![](D:/vault/강의/생성형AI/attachments/genAI-3d_texture.png)

## 캐릭터 / 만화

![](D:/vault/강의/생성형AI/attachments/genAI-character_cartoon.png)

## 레퍼런스: TV쇼/만화영화

![](D:/vault/강의/생성형AI/attachments/genAI-ref_tv_shows_anime.png)

## 레퍼런스: 유명 일러스트레이터

![](D:/vault/강의/생성형AI/attachments/genAI-illustrators.png)

# 미술

## 고대, 중세, 암흑기

![](D:/vault/강의/생성형AI/attachments/genAI-early_art.png)

## 르네상스-근대

![](D:/vault/강의/생성형AI/attachments/genAI-renaissance_modern.png)

## 근대(modern)

![](D:/vault/강의/생성형AI/attachments/genAI-modern_arts.png)

---

## 근대(modern)

![](D:/vault/강의/생성형AI/attachments/genAI-modern_arts2.png)

## 레퍼런스: 예술가

![](D:/vault/강의/생성형AI/attachments/genAI-artist_tests.png)

---

## 레퍼런스: 예술가

![](D:/vault/강의/생성형AI/attachments/genAI-distinctive_artists.png)

# 3D 아트웤

## 조각 / 동상

![](D:/vault/강의/생성형AI/attachments/genAI-sculpture_statues.png)

## 착용하거나 인체에 장착하는 것들

![](D:/vault/강의/생성형AI/attachments/genAI-things_for_human_bodies.png)

## 장소 / 공간

![](D:/vault/강의/생성형AI/attachments/genAI-places_and_spaces.png)

## 공예: 종이 / 자수

![](D:/vault/강의/생성형AI/attachments/genAI-crafty_paper_textiles.png)

## 공예: 자기 / 유리

![](D:/vault/강의/생성형AI/attachments/genAI-ceramics_glasses.png)

## 실사 프롬프트와 조합

![](D:/vault/강의/생성형AI/attachments/genAI-photographing_art.png)