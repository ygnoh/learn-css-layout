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

