### flex

- flex box / flexible box (유연한) 레이아웃을 위한 방식 -> 기존의 `inline` 보다 막강!
- `grid`는 `flex` 보다 조금 더 막강 ㅎㅎ
- 하지만! `flex` 만으로 가능한 레이아웃이 있음. 두개의 특징을 잘 알고 적재적소에 둘 다 활용하는게 가장 BEST
- IE는 10과 11에서 부분 지원

### flex layout 을 위한 기본적인 HTML 구조

```html
<div class="container">
  <div class="item">item1</div>
  <div class="item">item2</div>
  <div class="item">item3</div>
</div>
```

- 부모를 container
- 자식을 item
- 컨테이너는 flex의 영향을 받는 전체 공간이고, 설정된 속성에 따라 각각의 아이템들이 배치된다.
- `flex` 속성들은 컨테이너에 적용하는 속성, 아이템에 적용하는 속성 이렇게 두가지로 나뉜다.

### Container에 적용하는 속성

**1. display: flex**

![image](https://user-images.githubusercontent.com/39187116/100558650-a06e7500-32f2-11eb-8a5b-2790b55631f3.png)

- `flex` 아이템들은 가로방향으로 배치된다.
- 각 아이템들의 width는 자신이 가진 내용물의 width 만큼만 차지
- `float` 의 경우 자신의 내용물이 가진 높이 만큼의 height을 갖지만, `flex` 는 컨테이너의 높이를 따라간다 -> 컬럼들의 높이가 자동으로 다 맞춰진다.

**2. display: inline-flex**

![image](https://user-images.githubusercontent.com/39187116/100558673-b0865480-32f2-11eb-91fe-60d7b8236455.png)

- `flex` 와 비슷하게 동작하지만 컨테이너가 inline으로 동작한다.

**3. flex-direction**

**메인축**의 방향을 결정한다.

> 메인(main)축 ? `flex` 아이템들이 배치된 방향.

- 기본값은 `row`

```
A B C
```

- `column` 으로 하면 메인축의 방향이 세로로 바뀐다.

```
A
B
C
```

- `row-reverse`

```
C B A
```

- `column-reverse`

```
C
B
A
```

**4. flex-wrap**

- 컨테이너가 더 이상 아이템을 한 줄에 담을 여유공간이 없을 때 줄바꿈을 할지? 말지? 결정!
- 기본값은 `nowrap` : 줄바꿈을 하지 않는다. 넘치면 그냥 삐져 나감
- `wrap` : 줄바꿈을 한다. `inline-block` 처럼 동작한다.

```
A B
C D
```

- `wrap-reverse` : 줄바꿈을 한다. 단, 아이템을 역순으로 배치한다.

```
C D
A B
```

**5. flex-flow**

- `flex-direction` 과 `flex-wrap` 을 한꺼번에 지정할 수 있다.
- `flex-direction` , `flex-wrap` 순서대로 써주면 된다.

```css
.flex-container {
  flex-flow: row wrap;
}
```

**6. justify-content (정렬)**

```
- justify는 메인 축을 기준으로 아이템 정렬
- align은 메인 축과 수직이 되는 수직 축을 기준으로 아이템을 정렬
```

- `flex-start` : default 옵션, 아이템을 시작점으로 정렬한다.

![image](https://user-images.githubusercontent.com/39187116/100679852-c0b23880-33b3-11eb-9efa-f71ca309709b.png)

이때, `flex-direction` 이 `column` 인 경우 위 에서 부터 정렬한다.

- `flex-end`: 아이템을 끝점으로 정렬한다.

![image](https://user-images.githubusercontent.com/39187116/100680031-1090ff80-33b4-11eb-8ba2-be032258b821.png)

이때, `flex-direction` 이 `column` 인 경우 아래에서 부터 정렬한다.

- `center` : 가운데로 정렬한다.

![image](https://user-images.githubusercontent.com/39187116/100680139-4930d900-33b4-11eb-88f3-3757ad3a1afc.png)

- `space-between` : 아이템들의 사이에 균일한 간격을 만들어 준다.

![image](https://user-images.githubusercontent.com/39187116/100680231-72ea0000-33b4-11eb-8b8e-bff46ec4d112.png)

- `space-around`: 아이템들의 둘레에 균일한 간격을 만들어 준다.

![image](https://user-images.githubusercontent.com/39187116/100680365-bf354000-33b4-11eb-881a-1310f142c0c4.png)

- `space-evenly`: 아이템들의 사이와 양 끝에 균일한 간격을 만들어 준다.

![image](https://user-images.githubusercontent.com/39187116/100680468-f60b5600-33b4-11eb-96cc-d0b20433c0b1.png)

단, 이 속성은 **IE와 Edge에서는 지원하지 않는다!**

**6. align-items (정렬)**

메인축과 수직이 되는 수직축을 기준으로 정렬한다!

- `strecth` : default 옵션, 아이템들을 수직축 방향으로 쫘~악 늘린다. 이 옵션으로 인해, 아이템들이 컨테이너의 높이에 따라서 쫙 채워지는 것
- `flex-start` : 아이템을 수직축의 시작점으로 정렬한다.
- `flex-end`: 아이템을 수직축의 끝점으로 정렬한다.
- `center`: 아이템을 수직축의 중앙으로 정렬한다.
- `baseline`: 아이템을 텍스트 베이스라인 기준으로 정렬한다.

![image](https://user-images.githubusercontent.com/39187116/100680958-0a9c1e00-33b6-11eb-916a-cb464f7ae5f2.png)

<div style="width: 100%; text-align: center;"><a href="https://velog.io/@ursr0706/vertical-align">출처</a></div>

**6.5 아이템 한 가운데에 정렬하기**

- `justify-content: center; align-items: center;` 를 이용하면 아이템을 쉽게 컨테이너 중앙에 정렬 가능하다.
- 아이템 이미지가 균일하지 않을 때 이 옵션을 이용해서 정렬하면 유용하다. ( padding 으로는 힘들쥐 )

```css
display: inline-flex;
justify-content: center;
align-items: center;
width: 30px;
height: 30px;
```

**7. align-content**

`flex-wrap: wrap` 이 설정된 상태에서, flex 아이템들의 행이 2줄 이상 되었을 때 **수직축 방향 정렬**을 어떻게 할 것인지 결정!

- default 값은 `stretch` : 쫙 늘린다. 이때 부모의 height을 각 행들이 나눠 갖는다.
- `flex-start`

<img src="https://user-images.githubusercontent.com/39187116/100758681-209bf400-3433-11eb-8ef8-bb9d372a7f07.png" width="300" height="300" />

- `space-between`

<img src="https://user-images.githubusercontent.com/39187116/100758988-783a5f80-3433-11eb-980e-d84364c07e41.png" width="300" height="400"/>

- `align-items` 에서 옵션들을 설명했던 것 처럼, `flex-end`, `space-around` , `center` , `space-evenly` 모두 같은 방식으로 정렬된다. `space-evenly` 는 ms 계열 브라우저에서 지원하지 않는다!

<br/>
<br/>

### flex 아이템에 적용하는 속성

**1. flex-basis**

- flex 아이템의 **기본** 크기를 설정한다.
- `flex-direction` 이 row일 때는 width, column인 경우는 높이를 설정
- 단위로는 css width, height 속성에 사용하는 각종 단위의 수가 들어갈 수 있다.
- `default` 값은 auto 이며 width 속성 값을 사용한다. 만약 width를 따로 설정하지 않으면 content의 크기를 따라간다.
- `content` 로 값을 부여하면, 컨텐츠의 크기를 따라간다. 이는 width를 따로 설정하지 않은 경우와 같다.

**2. flex-grow**

- `flex-basis`보다 커질 수 있는지를 결정하는 속성
- 0보다 크면 해당 아이템은 유연한 flexible 박스가 된다.
- `default` 값이 0이기 대문에, 따로 적용하기 전까지는 아이템이 늘어나지 않음.
- `flex-grow` 에 들어간 숫자의 의미는, 아이템들의 `flex-basis` 를 제외한 여백 부분을 **flex-grow에 지정된 숫자의 비율로 나누어** 가진다.

![image](https://user-images.githubusercontent.com/39187116/102730813-4a34a500-4379-11eb-82a0-5ee8fb9dfafe.png)

```css
.item {
  flex-grow: 1;
}
```

각 아이템들의 여백 비율을 1:1:1로 설정

![image](https://user-images.githubusercontent.com/39187116/102730930-a697c480-4379-11eb-9bbd-b340c047028d.png)

```css
.item {
  flex-grow: 1;
}
.item:nth-child(2) {
  flex-grow: 2;
}
```

아이템들의 여백 비율을 1:2:1로 설정

**3. flex-shrink**

- `flex-grow` 와 쌍을 이루는 속성. `flex-basis` 값 보다 작아질 수 있는지를 결정한다.
- `default` 값은 1이다. 0보다 크면 `flex-basis` 보다 작아질 수 있는 flexible한 박스가 된다.
- 0으로 세팅하면 아이템의 크기가 `flex-basis`보다 작아지지 않는다. (고정폭의 칼럼을 만들때 유용)

**4. flex**

- `flex-grow`, `flex-shrink`, `flex-basis` 를 한번에 쓸 수 있는 축약형

```css
.item {
  flex: 1;
  /* flex-grow: 1; flex-shrink: 1; flex-basis: 0%; */
  flex: 1 1 auto;
  /* flex-grow: 1; flex-shrink: 1; flex-basis: auto; */
  flex: 1 500px;
  /* flex-grow: 1; flex-shrink: 1; flex-basis: 500px; */
}
```

- 주의할 점은 `flex-basis` 를 생략하게 되면 `flex-basis` 의 값은 **0%**가 된다.

<br/>

### 개별 아이템을 정렬하기

**1. align-self**

- `align-items` 의 아이템 버젼 속성이다.
- 기본값은 `auto`로서, `align-items` 속성을 상속 받는다.
- `align-self`는 `align-items`보다 우선순위가 높다.
- 기본적인 속성 값의 동작은 `align-items`와 같다.

```css
.flex-container {
  display: flex;
  height: 300px;
  align-items: flex-end;
}

.flex-item:nth-child(2) {
  align-self: flex-start;
}
```

![image](https://user-images.githubusercontent.com/39187116/102782172-3d956880-43dc-11eb-8890-979413fe1718.png)

**2. 아이템의 배치 순서 order**

- 말 그대로 아이템의 순서를 결정

```css
.flex-container {
  display: flex;
}
.flex-item:nth-child(1) {
  order: 3;
}
.flex-item:nth-child(2) {
  order: 100000;
}
.flex-item:nth-child(3) {
  order: 2;
}
```

- **시각적**인 순서일 뿐, HTML 자체의 구조를 바꾸는 것은 아니여서 웹 접근성 측면에서 주의해야한다.
- 숫자가 작을수록 먼저 배치된다.
- C -> A - > B 순서

**3. z-index**

- `display-flex`가 컨테이너에 있으면, 사용할 수 있다.
- 기본값은 0
- 기존에 사용하던 z-index와 같은 방식으로 동작한다.

<br/>

### 유용한 기법들

**1. 아이템 1개만 오른쪽으로 나열하기**

```css
.flex-container {
  display: flex;
}

.flex-item {
  width: 150px;
}

.flex-item:last-child {
  margin-left: auto;
}
```

![image](https://user-images.githubusercontent.com/39187116/102736249-cc2bca80-4387-11eb-96cd-9e0c73fcf3e8.png)

- 원리: `margin` 을 auto로 주면 남아있는 `margin` 을 모두 소비한다.
- Block 요소에 `margin: 0 auto` 를 줘서 중앙 정렬 하는 방식과 같은 원리이다.

**2. 고정폭 칼럼과 가변폭 칼럼을 함께 만들기**

```css
.flex-container {
  display: flex;
}

.flex-item:nth-child(1) {
  width: 150px;
  flex-shrink: 0;
}
.flex-item:nth-child(2) {
  flex-grow: 1;
}
.flex-item:nth-child(3) {
  width: 250px;
  flex-shrink: 0;
}
```

- `flex-shrink` 속성을 0으로 할당해서 브라우저 크기가 줄어들 때 아이템이 flexible에 줄어드는 것을 막았다.
- 두번째 요소에는 `flex-grow` 를 1로 줘서 브라우저 크기가 늘어날 때 아이템이 flexible하게 넓어지도록 설정.

**3. 푸터 하단에 고정시키기**

예제 마크업

```html
<div class="page">
  <header>header</header>
  <section class="content">샬라샬라</section>
  <footer>footer</footer>
</div>
```

- `flex-grow` 을 이용해서 content 길이를 채워주는게 핵심!

```css
.page {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}

.content {
  flex-grow: 1;
}
```

- 컨테이너가 최소 높이가 있어야 content 의 `flex-grow` 에 값을 줬을 때 잘 채워진다.
- 인터넷 익스플로어 11에서는 `min-height` 에 flex 정렬 옵션을 주면 올바르게 동작하지 않는 버그가 있다. 이런 경우 `min-height` 대신 `height` 을 주고 content에 `overflow` 속성을 주자!!
