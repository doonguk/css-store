## 그냥 정리

**base-menu**
- a태그의 `font-size`에 맞는 padding을 위해 em 사용
- `flex-grow`를 이용한 transition은 IE에서 이슈가 있기 때문에, width를 사용
<br/><br/>

**search-input**
- 검색을 위해 input type을 `search` 사용
- html root element의 기본 font-size는 16px;
- `rem`을 사용하면 root element를 기준으로 설정
- `em`은 스타일을 지정한 요소의 폰트 크기를 곱한 값
```css
.item {
  padding: 0.5em;
}
```
예를들어 위 코드에서 item 클래스가 갖는 패딩은 16px * 0.5 = 8px이다.
<br/><br/>

**bullet-list**
- bullet을 인라인 요소로 만들기보다 가상엘리먼트 `before` 사용
- 가상 엘리먼트와 text를 flex-item 으로 사용하는 아이디어
<br/><br/>

**message-list**
- user 이미지를 표현하기 위해 `figure` 태그 사용
- `figure`태그 안에 유저마다 다른 이미지 크기를 가질 수 있기 때문에 `img`태그를 사용하지 않고 `background`로 설정
- `figure`의 기본 크기를 보장하기 위해 `flex-shirink` 사용
<br/><br/>

**user-list**
- 핵심은 아래
```css
  .user-name {
      overflow: hidden;
      text-overflow:ellipsis;
      white-space: nowrap;
    }
```

**card-list**
- 반응형 카드 리스트를 위해서 figure 영역에 세로 패딩을 적용(`padding-bottom: 60%`)
- `width`가 600px 이상인 경우 좌우 패딩을 없애기 위해 컨테이너에 마이너스 margin 적용
- 모든 card-desc 부분의 height을 맞추기 위해 `flex-grow` 사용 (알아서 늘어나게~)


**index**
- `~`는 형제 선택자 (모두 선택)
- `+`도 형제 선택자 (바로 다음에 나오는 형제 1개만 선택, 다음에 다른거 나오면 선택안됨ㅠ)
- `checkbox`의 `checked` 속성에 css를 적용해서 모달 on / off 구현
- seo / 스크린리더기 생각해서 label의 text를 display `none` 하지 않고, `absolute + 1px + 1px + hidden` 조합으로 숨김 
- `width`가 딱 정해진 친구들은 `flex-grow`보다 % 사용하는게 좋음. 예를들어 어떤 레이아웃이 `300px + flex-grow:1 + 300px` 구조로 한 줄에 있다면, 브라우저 렌더링 순서상 300px 채우고 grow로 남은 영역 채우고 다음 줄에서 300px을 그리기 때문에 올바른 레이아웃을 만들 수 없음.
- view-port가 1024px 이상인 경우 `order` 속성을 이용해서 flex-item 을 재배치, 이때 속성을 지정해주지 않은 아이템은 `order` 값이 0으로 우선순위가 가장 높다.