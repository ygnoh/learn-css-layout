# learn-css-layout
http://ko.learnlayout.com/

## display

### block
div, p, form, header, footer, section

### inline
span, a

### none
마치 엘리먼트가 없는 것처럼 페이지가 렌더링 됨. 하지만 visibility: hidden;은 엘리먼트는 감춰지지만 여전히 공간을 차지함

### inline-block, flex
나중에 살펴봄

### 재정의 가능
언제든지 display 기본값을 재정의할 수 있음

## margin: auto;
블록 엘리먼트를 width를 주어 크기를 지정하고, 좌우 마진을 auto로 주면 해당 컨테이너의 가로 중앙에 오게 됨
```css
#main {
    width: 600px;
    margin: auto;
}
```

## max-width
위의 상황에서 width 대신 max-width를 사용하면 창의 폭이 width보다 작을 때에 대해 개선할 수 있음
```css
#main {
    max-width: 600px;
    margin: auto;
}
```

## 박스 모델
엘리먼트 너비를 설정할 때 내가 설정한 것보다 크게 나타날 수 있음. 엘리먼트의 테두리와 패딩 때문.
```css
.simple {
    width: 500px;
    margin: 20px auto;
}

/* 위 아래 모두 동일한 크기를 지정했지만 다르게 나타남 */

.fancy {
    width: 500px;
    margin: 20px auto;
    padding: 50px;
    border-width: 10px;
}
```

오랫동안 이 문제의 해결법은 너비값을 조절하는 것이었음. 더는 그렇게 하지 않아도 됨

## box-sizing
엘리먼트에 box-sizing을 지정하면 패딩과 테두리가 너비를 늘이지 않음

```css
.simple {
    width: 500px;
    margin: 20px auto;
    -webkit-box-sizing: border-box;
    -moz-box-sizing: border-box;
    box-sizing: border-box;
}

/* 위 아래 모두 크기가 동일함 */

.fancy {
    width: 500px;
    margin: 20px auto;
    padding: 50px;
    border-width: 10px;
    -webkit-box-sizing: border-box;
    -moz-box-sizing: border-box;
    box-sizing: border-box;
}
```

## position

### static
position 기본값. "위치가 지정되지 않았다"라는 의미.
```css
.static {
    position: static;
}
```

### relative
```css
.relative1 {
    position: relative;
}

.relative2 {
    position: relative;
    top: -20px;
    left: 20px;
    background-color: white;
    width: 500px;
}
```

relative는 별도의 위치 프로퍼티를 지정하지 않는 이상 static과 동일하게 동작합니다.
top, right, bottom, left를 지정하면 위치가 조정됨.

### fixed
viewport에 상대적으로 위치가 지정됨. top, right, bottom, left로 위치 지정.
```css
.fixed {
    position: fixed;
    bottom: 0;
    right: 0;
    width: 200px;
    background-color: white;
}
```

### absolute
"위치가 지정된" 가장 가까운 곳에 위치한 조상 엘리먼트에 대해 위치를 지정함.
그런 엘리먼트가 없으면 document body를 기준으로 함.
```css
.relative {
    position: relative;
    width: 600px;
    height: 400px;
}

.absolute {
    position: absolute;
    top: 120px;
    right: 0;
    width: 300px;
    height: 200px;
}
```

## 위치 지정 예제
```css
.container {
    position: relative;
}
nav {
    position: absolute;
    left: 0px;
    width: 200px;
}
section {
    margin-left: 200px;
}
footer {
    position: fixed;
    bottom: 0;
    left: 0;
    height: 70px;
    background-color: white;
    width: 100%;
}
body {
    margin-bottom: 120px;
}
```

## float
레이아웃 잡는 데 사용되는 또 다른 CSS 프로퍼티. 이미지 주위를 텍스트로 감싸게 하기 위해 쓰임
```css
img {
    float: right;
    margin: 0 0 1em 1em;
}
```

## clear
float의 동작 방식을 제어하는데 중요. float를 주게되면 엘리먼트가 떠있게 되고, 이로 인해 다른 엘리먼트(자식이 아닌데도)에 영향을 줌.
이때 다른 엘리먼트에 clear를 적용하여 float 영향을 제거할 수 있음

## clearfix 핵
float를 적용한 엘리먼트가 부모 보다 크기가 크면 바깥으로 넘치는 현상 발생.
이 때 부모 엘리먼트에 overflow: auto;를 주어서 해결(clearfix 핵).

## 퍼센트 너비
컨테이너에 대하여 상대적인 너비 지정

### 퍼센트 너비 레이아웃
레이아웃을 잡는 데 퍼센트를 쓸 수도 있지만 그러면 작업량이 많아질 수 있음. 콘텐츠에 알맞는 방식을 선택해야 함.

## 미디어 쿼리
브라우저와 디바이스에 반응하는 사이트를 만들 수 있음
```css
@media screen and (min-width: 600px) {
    nav {
        float: left;
        width: 25%;
    }
    section {
        margin-left: 25%;
    }
}
@media screen and (max-width: 599px) {
    nav li {
        display: inline;
    }
}
```

### 보충 설명
meta viewport를 이용하면 모바일에서도 더 나은 모습으로 보이게 할 수 있음

