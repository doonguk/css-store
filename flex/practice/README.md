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