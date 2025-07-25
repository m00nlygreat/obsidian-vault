---
title: UI 엘리먼트
author: 배문형
type: module
tags:
  - 서비스기획
---

## UI를 뜯어보는 기준

- Looks: 어떻게 생겼는지
	- Status: 어떤 상태를 가지는지
- Interact: 어떤 인터랙션을 가지는지
- Data: 어떤 데이터가 암시되어 있는지

![](../attachments/uxdesign-ui_status.png)

# Primitives

## Button

#### Looks

- 누를 수 있는 사각형의 영역과 버튼의 기능을 설명하는 레이블
	- 간혹 아이콘을 포함하기도
- Hover, Pressed(Active)
- 공통: Enabled/Disabled, Focused/Focused not, Empty/Filled, Validated, not Validated

#### Interact

- Activate
	- 누르기
	- 떼기

***

#### Data

- onClick : function()

---

![](../attachments/uxdesign-buttons.png)

## Radio Button

### Looks

- 눌렀을 때 속이 채워지는 동그란 버튼과 레이블
	- 이것이 여러 개 있음
- Checked, Checked not

### Interact

- Activate

### Data

- items: Item[]
- selected: Item

![](../attachments/uxdesign-radio_buttons.png)

## Checkbox

### Looks

- 빈 사각형에 체크마크, 그리고 레이블
- Checked, Checked not, (Indeterminate)

### Interact

 - Activate, Deactivate

### Data

- checked: boolean

![](../attachments/ux-checkboxes.png)

## Switch

### Looks

- 현실세계의 on/off 스위치를 본따, 핸들이 있고 핸들의 가동 범위 안에서 on/off의 영역이 있음
- Activated / Deactivated

### Interact

- Activate, Deactivate

### Data

- activated: boolean

![](../attachments/ux-switches.png)

## Input

### Looks

- 사각형의 입력 영역, Placeholder, Title, Cursor, (Icon), (alert)
- Empty, Filled, Error, Accepted

### Interact

- Activate
- Enter
- Validate

### 모바일에서

- [인풋 입력 시 적절한 키보드가 나와야 한다.](http://mobileinputtypes.com/)

![](../attachments/ux-inputs.png)

## Slider

- 핸들과 핸들의 1차원 가동범위. 스텝 눈금
	- Range Variant
- 스텝(Steps)
- 스크롤바도 일종의 슬라이더?


### Interact

- Set

### Data

- value: number

#### 난 슬라이더가 싫어요

![](../attachments/ux-sliders.png)

## Progresss bar

### Looks

- 진행상태를 나타내는 막대
- 보통 전체를 현재 진행이 채우는 형태로 작성
- Completed / In Progress / Stuck

### Interact

- 끝나기를 기다리며 하염없이 쳐다보기

### Data

- value: 0<number<=1
	- .. 인데 이 number 계산을 어떻게 하느냐가 중요

![](../attachments/ux-elements_progress_bars.png)

## Dropdown ≒ Selectbox, Combobox

### Looks

- 누름틀과 누르면 열리는 리스트
- Open / not open

### Interact

- Click to open
- Set

### Data

- items: Item[]
- selected: Item

![](../attachments/uxdesign-selectBox.png)

# Composites

## Scroll or Pan

- 표시할 수 있는 영역보다 컨테이너가 포함한 콘텐츠가 클 때 등장하는 인터랙션

### Scroll Bar

- 윈도우와 맥에서 동작 다름

### Inner Scroll

- 스크롤이 중첩되는 것은 최악의 UX

![](../attachments/ux-scroll.png)

## Form

- 특정 목적의 데이터들을 입력받는 인풋들의 집합 (예: 회원가입)

![](../attachments/uxdesign-forms.png)

## Tab

- 여러 페이지들을 묶어 버튼으로 전환할 수 있도록 추상화한 컨테이너 요소
- 탭 중첩 (Nested Tab) 주의

![](../attachments/uxdesign-tabs.png)

## Dialog

- 대화상자. 

![](../attachments/ux-elements_dialogues.png)

## Modal ≒ Window

- 현재 맥락과 구분되는 특정한 목적을 가지고 실행되는 독립된 작은 창
- 실행시 부모 컨테이너의 Interaction 중단됨 ≠ Modeless
- Pop-ups / Pop-over

#### 닫히면 안되는 팝업

- 2차 인증번호를 입력하는 Modeless 팝업?

![](../attachments/ux-popups.png)


## Screen / Page

- 페이지의 구분과 논리적 위계는 **자의적**임
- 왼쪽 -> 오른쪽
	- 이전 -> 이후
	- 큰 것 -> 작은 것
	- Public -> Private
- 유저가 길을 잃지 않게 하기
	- 논리적인 위계
	- Breadcrumbs
	- One Page One Thing
	- Single Column
	- 카드소팅(Card Sorting)

![](../attachments/ux-screens.png)

## List

- 여러 개의 항목을 보여주는 컨테이너
- Swipe actions

![](../attachments/ux-lists.png)

---

### 다양한 기기에서의 List

![](../attachments/ux-lists_on_devices.png)

## Card

- 프로퍼티를 가진 복수 개의 복잡한 정보를 나타내는 효과적인 UI 요소
- Flat UI의 핵심

![](../attachments/ux-cards.png)

## Popup / Context Menu

- 우클릭하면 나타나는 상황에 맞는 (Contextual) 메뉴
- Dropdown과 비슷하게 메뉴 출현 위치에 대해 고민 필요

![](../attachments/ux-context_menu.png)

## 기타

- Splash Screen
- Accordion
- Focus
- Icon
- Carousel
- Dashboard
- Navigation Bar / Top App Bar
- Tab Bar / Navigation Bar
- Notification Bar
- Stepper / Spinner

***

- Toast
- Banner
- Popper
	- Popover
- Tooltip
- Bottom Sheet
	- Grabber
- Floating Action Button
- CTA Button
- Skeleton
- Sticky Header

## 왠진 모르겠지만 음식 이름으로 부름

- Hamburger
- Kebob
- Bento
- Toast
- Breadcrumbs

![](../attachments/ux-know_your_menu.png)

## 이름에 집착하지 맙시다

- UI 요소, 인터랙션의 정확한 이름은 찾기도 어렵고 **팀원 간 합의도 어려움**
- 따라서 혼자 정확한 이름을 쓰는 고집을 부렸을 때의 이득은 그냥 '멋있어 보인다'뿐.
- 중요한 것은 팀 내에서의 소통입니다