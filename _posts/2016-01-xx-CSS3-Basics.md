---
layout: post
title: CSS3 Basics
categories: css
---

* TOC
{:toc}

# 1. 선택자 (Selector)

CSS (Cascading Style Sheets) 는 HTML 요소(Element)의 style(design, layout etc)을 정의한다. 그리하려면 HTML이 존재하여야 하고 또한 style을 지정하고자하는 HTML 요소를 특정할 필요가 있다.

이러한 목적으로 사용되는 것이 선택자(Selector)이다. 즉, style을 지정하고자하는 HTML 요소를 선택하는 기능을 하는 것이다.

![css selector](/img/css-syntax.png)

복수개의 선택자를 연속하여 지정할 수 있으며 쉼표( , )로 구분한다.

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      h1 { color: red; }
      p  { color: blue; }
    </style>
  </head>
  <body>
    <h1>Hello World!</h1>
    <p>This paragraph is styled with CSS.</p>
  </body>
</html>
```

## 1.1 전체 선택자 (Universal Selector)

HTML 문서 내의 모든 요소를 선택한다. html 요소에 포함된 모든 요소가 선택된다. (head 요소도 포함된다)

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      * {
        background-color: yellow;
      }
    </style>
  </head>
  <body>
    <h1>Welcome to My Homepage</h1>
    <div class="intro">
      <p id="firstname">My name is Donald.</p>
      <p id="hometown">I live in Duckburg.</p>
    </div>
    <p>My best friend is Mickey.</p>
  </body>
</html>
```

## 1.2 태그 선택자 (Type Selector)

특정한 태그명을 가지는 요소를 선택한다.

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      p {
        background-color: yellow;
      }
    </style>
  </head>
  <body>
    <h1>Welcome to My Homepage</h1>
    <div class="intro">
      <p id="firstname">My name is Donald.</p>
      <p id="hometown">I live in Duckburg.</p>
    </div>
    <p>My best friend is Mickey.</p>
  </body>
</html>
```

## 1.3 ID 선택자 (ID Selector)

id 속성값을 지정하여 일치하는 요소를 선택한다. id 속성값은 중복되지 않는 유일한 값이어야 한다.

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      #firstname {
        background-color: yellow;
      }
    </style>
  </head>
  <body>
    <h1>Welcome to My Homepage</h1>
    <div class="intro">
      <p id="firstname">My name is Donald.</p>
      <p id="hometown">I live in Duckburg.</p>
    </div>
    <p>My best friend is Mickey.</p>
  </body>
</html>
```

## 1.4 클래스 선택자 (Class Selector)

class 속성값을 지정하여 일치하는 요소를 선택한다. class 속성값은 중복될 수 있는 값이다.

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      .intro {
        background-color: yellow;
      }
    </style>
  </head>
  <body>
    <h1>Welcome to My Homepage</h1>
    <div class="intro">
      <p id="firstname">My name is Donald.</p>
      <p id="hometown">I live in Duckburg.</p>
    </div>
    <p>My best friend is Mickey.</p>
  </body>
</html>
```

class 속성값은 복수개 지정할 수 있다.(공백으로 구분)

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      /* p 태그 중 class 속성값이 center인 요소 */
      p.center {
        text-align: center;
        color: red;
      }

      p.large {
        font-size: 300%;
      }
    </style>
  </head>
  <body>
    <h1 class="center">This heading will not be affected</h1>
    <p class="center">This paragraph will be red and center-aligned.</p>
    <p class="center large">This paragraph will be red, center-aligned, and in a large font-size.</p>
  </body>
</html>
```

## 1.5 속성 선택자 (Attribute Selector)

특정 속성을 지정하여 일치하는 요소를 선택한다.

| 패턴                 | Description |
|:--------------------|:------------|
| 선택자[속성]           | 지정 속성과 일치하는 요소 선택
| 선택자[속성=값]        | 지정 속성과 값이 일치하는 요소 선택
| 선택자[속성~=값]       | 지정 속성값을 단어로 포함하는 요소 선택
| 선택자[속성\|=값]       | 지정 속성값과 단어로 일치하거나 지정 속성값으로 시작하는 요소 선택
| 선택자[속성^=값]       | 지정 속성값으로 시작하는 요소 선택
| 선택자[속성$=값]       | 지정 속성값으로 끝나는 요소 선택
| 선택자[속성*=값]       | 지정 속성값을 포함하는 요소 선택

선택자[속성]

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      a[href] {
        background-color: yellow;
      }
    </style>
  </head>
  <body>
    <a href="http://www.w3schools.com">w3schools.com</a><br>
    <a href="http://www.disney.com" target="_blank">disney.com</a><br>
    <a href="http://www.wikipedia.org" target="_top">wikipedia.org</a>
  </body>
</html>
```

선택자[속성=값]

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      a[target=_blank] {
        background-color: yellow;
      }
    </style>
  </head>
  <body>
    <a href="http://www.w3schools.com">w3schools.com</a><br>
    <a href="http://www.disney.com" target="_blank">disney.com</a><br>
    <a href="http://www.wikipedia.org" target="_top">wikipedia.org</a>
  </body>
</html>
```

선택자[속성~=값]

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      h1[title~=first] {
        background-color: yellow;
      }
    </style>
  </head>
  <body>
    <h1 title="heading first">Heading first</h1>
    <h1 title="heading second">Heading second</h1>
    <h1 title="heading third">Heading third</h1>
  </body>
</html>
```

선택자[속성\|=값]

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      [lang|=en] {
        background: yellow;
      }
    </style>
  </head>
  <body>
    <p lang="en">Hello!</p>
    <p lang="en-us">Hi!</p>
    <p lang="en-gb">Ello!</p>
    <p lang="us">Hi!</p>
    <p lang="no">Hei!</p>
  </body>
</html>
```

선택자[속성^=값]

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      div[class^=test] {
        background: #ffff00;
      }
    </style>
  </head>
  <body>
    <div class="first_test">The first div element.</div>
    <div class="second">The second div element.</div>
    <div class="test">The third div element.</div>
    <p class="test">This is some text in a paragraph.</p>
  </body>
</html>
```

선택자[속성$=값]

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      div[class$=test] {
        background: #ffff00;
      }
    </style>
  </head>
  <body>
    <div class="first_test">The first div element.</div>
    <div class="second">The second div element.</div>
    <div class="test">The third div element.</div>
    <p class="test">This is some text in a paragraph.</p>
  </body>
</html>
```

선택자[속성*=값]

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      div[class*=test] {
        background: #ffff00;
      }
    </style>
  </head>
  <body>
    <div class="first_test">The first div element.</div>
    <div class="second">The second div element.</div>
    <div class="test">The third div element.</div>
    <p class="test">This is some text in a paragraph.</p>
  </body>
</html>
```

## 1.6 복합 선택자 (Combinator)

### 1.6.1 후손 선택자 (Descendant Combinator)

![css descendant child combinator](/img/descendant-child.png)

자신의 1 level 상위에 속하는 요소를 부모 요소, 1 level 하위에 속하는 요소를 자손 요소(자식 요소)라한다.

자신보다 n level 하위에 속하는 요소는 후손 요소(하위 요소)라 한다.

```
선택자A 선택자B
```

후손 선택자는 선택자A의 모든 후손(하위) 요소 중 선택자B와 일치하는 요소를 선택한다.

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      div p {
        background-color: yellow;
      }
    </style>
  </head>
  <body>
    <h1>Welcome to My Homepage</h1>

    <div>
      <h2>My name is Donald</h2>
      <p>I live in Duckburg.</p>
      <span><p>I will not be styled.</p></span>
    </div>

    <p>My best friend is Mickey.</p>
  </body>
</html>
```

### 1.6.2 자손 선택자 (Child Combinator)

```
선택자A > 선택자B
```

자손 선택자는 선택자A의 모든 자손(자식) 요소 중 선택자B와 일치하는 요소를 선택한다.

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      div > p {
        background-color: yellow;
      }
    </style>
  </head>
  <body>
    <h1>Welcome to My Homepage</h1>

    <div>
      <h2>My name is Donald</h2>
      <p>I live in Duckburg.</p>
      <span><p>I will not be styled.</p></span>
    </div>

    <p>My best friend is Mickey.</p>
  </body>
</html>
```

### 1.6.3 동위 선택자

```
선택자A + 선택자B
```
선택자A 바로 뒤에 위치하는 선택자B 요소를 선택한다.

```
선택자A ~ 선택자B
```
선택자A 뒤에 위치하는 모든 동위 요소 중 선택자B와 일치하는 요소를 선택한다.

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      p + ul {
        color: red;
      }

      p ~ ul {
        background: yellow;
      }
    </style>
  </head>
  <body>
    <div>A div element.</div>
    <ul>
      <li>Coffee</li>
      <li>Tea</li>
      <li>Milk</li>
    </ul>

    <p>The first paragraph.</p>
    <ul>
      <li>Coffee</li>
      <li>Tea</li>
      <li>Milk</li>
    </ul>

    <h2>Another list</h2>
    <ul>
      <li>Coffee</li>
      <li>Tea</li>
      <li>Milk</li>
    </ul>
  </body>
</html>
```

## 1.7 가상 클래스 선택자 (Pseudo-Class Selector)

가상 클래스는 요소의 특정 상태에 따라 스타일을 정의할 때 사용된다. 특정 상태란 예를 들어 다음과 같다.

- 마우스가 올라와 있을때

- 링크를 방문했을 때와 아직 방문하지 않았을 때

- 포커스가 들어와 있을 때

가상 클래스는 마침표(.) 대신 콜론(:)을 사용한다. CSS 표준에 의해 미리 정의된 이름이 있기 때문에 임의의 이름을 사용할 수 없다.

```css
selector:pseudo-class {
  property: value;
}
```

다음은 div 요소가 hover 상태일 때(마우스가 올라와 있을 때) background-color를 blue로 지정하는 예이다.

```css
div:hover {
  background-color: blue;
}
```

### 1.7.1 링크 선택자(Link pseudo-classes), 동적 선택자(User action pseudo-classes)

| pseudo-class | Description   |
|:-------------|:--------------|
| :link        | 선택자가 방문하지 않은 링크일 때
| :visited     | 선택자가 방문한 링크일 때
| :hover       | 선택자에 마우스가 올라와 있을 때
| :active      | 선택자가 클릭된 상태일 때
| :focus       | 선택자에 포커스가 들어와 있을 때

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      /* unvisited link */
      a:link {
        color: orange;
      }

      /* visited link */
      a:visited {
        color: green;
      }

      /* mouse over link */
      a:hover {
        color: red;
      }

      /* selected link */
      a:active {
        color: blue;
      }
      </style>
    </head>
  <body>
    <a href="index.html" target="_blank">This is a link</a>
  </body>
</html>
```

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      input[type=text]:focus {
        background-color: yellow;
      }
    </style>
  </head>
  <body>
    First name: <input type="text" name="firstname"><br>
    Last name: <input type="text" name="lastname"><br>
    password: <input type="password" name="password">
  </body>
</html>
```

### 1.7.2 UI 요소 상태 선택자(UI element states pseudo-classes)

| pseudo-class | Description   |
|:-------------|:--------------|
| :checked     | 선택자가 체크 상태일 때
| :enabled     | 선택자가 사용 가능한 상태일 때
| :disabled    | 선택자가 사용 불가능한 상태일 때


```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      input:enabled + span {
        color: blue;
      }
      input:disabled + span {
        color: gray;
        text-decoration: line-through;
      }
      input:checked + span {
        color: red;
      }
    </style>
  </head>
  <body>
    <input type="radio" checked="checked" value="male" name="gender"> <span>Male</span><br>
    <input type="radio" value="female" name="gender"> <span>Female</span><br>
    <input type="radio" value="neuter" name="gender" disabled> <span>Neuter</span><hr>

    <input type="checkbox" checked="checked" value="bicycle"> <span>I have a bicycle</span><br>
    <input type="checkbox" value="car"> <span>I have a car</span><br>
    <input type="checkbox" value="motorcycle" disabled> <span>I have a motorcycle</span>
  </body>
</html>
```

### 1.7.3 구조 가상 클래스 선택자(Structural pseudo-classes)

| pseudo-class       | Description                          |
|:-------------------|:-------------------------------------|
| :first-child       | 선택자에 해당하는 모든 요소 중 첫번째 자식 요소
| :last-child        | 선택자에 해당하는 모든 요소 중 마지막 자식 요소
| :nth-child(n)      | 선택자에 해당하는 모든 요소 중 앞에서 n번째 자식 요소
| :nth-last-child(n) | 선택자에 해당하는 모든 요소 중 뒤에서 n번째 자식 요소

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      p:first-child {
        color: red;
      }
    </style>
  </head>
  <body>
    <p>This paragraph is the first child of its parent (body).</p>

    <h1>Welcome to My Homepage</h1>
    <p>This paragraph is not the first child of its parent.</p>

    <div>
      <p>This paragraph is the first child of its parent (div).</p>
      <p>This paragraph is not the first child of its parent.</p>
    </div>
  </body>
</html>
```

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      ol > li:nth-child(2n) {
        color: orange;
      }
      ol > li:nth-child(2n+1) {
        color: green;
      }
      ol > li:first-child {
        color: red;
      }
      ol > li:last-child {
        color: blue;
      }
      ol > li:nth-child(4) {
        background: brown;
      }

      ul > :nth-last-child(2n+1) {
        color: red;
      }
      ul > :nth-last-child(2n) {
        color: blue;
      }
    </style>
  </head>
  <body>
    <ol>
      <li>Espresso</li>
      <li>Americano</li>
      <li>Caffe Latte</li>
      <li>Caffe Mocha</li>
      <li>Caramel Latte</li>
      <li>Cappuccino</li>
    </ol>

    <ul>
      <li>Espresso</li>
      <li>Americano</li>
      <li>Caffe Latte</li>
      <li>Caffe Mocha</li>
      <li>Caramel Latte</li>
      <li>Cappuccino</li>
    </ul>
  </body>
</html>
```

| pseudo-class          | Description                          |
|:----------------------|:-------------------------------------|
| :first-of-type        | 선택자에 해당하는 모든 요소 중 첫번째에 등장하는 요소
| :last-of-type         | 선택자에 해당하는 모든 요소 중 마지막에 등장하는 요소
| :nth-of-type (n)      | 선택자에 해당하는 모든 요소 중 앞에서 n번째에 등장하는 요소
| :nth-last-of-type (n) | 선택자에 해당하는 모든 요소 중 뒤에서 n번째에 등장하는 요소

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      p:first-of-type {
        color: red;
      }
      p:last-of-type {
        color: blue;
      }
      p:nth-of-type(2) {
        color: green;
      }
      p:nth-last-of-type(2) {
        color: orange;
      }

      p:first-child {
        background: brown;
      }

    </style>
  </head>
  <body>
    <h1>This is a heading</h1>
    <p>The first paragraph.</p>
    <p>The second paragraph.</p>
    <p>The third paragraph.</p>
    <p>The fourth paragraph.</p>
  </body>
</html>
```

### 1.7.4 부정 선택자(Negation pseudo-class)

| pseudo-class          | Description                          |
|:----------------------|:-------------------------------------|
| :not(선택자)            | 선택자에 해당하지 않는 모든 요소

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      input:not([type=password]) {
        background: yellow;
      }
    </style>
  </head>
  <body>
    <input type="text" value="Text input">
    <input type="email" value="email input">
    <input type="password" value="Password input">
  </body>
</html>
```

## 1.8 가상 요소 선택자 (Pseudo-Element Selector)

가상 요소는 요소의 특정 부분에 스타일을 적용하기 위하여 사용된다. 특정 부분이란 예를 들어 다음과 같다.

- 요소의 첫글자 또는 첫줄

- 요소의 content 앞 또는 뒤

가상 요소에는 두개의 콜론(::)을 사용한다. CSS 표준에 의해 미리 정의된 이름이 있기 때문에 임의의 이름을 사용할 수 없다.

```css
selector::pseudo-element {
  property:value;
}
```

| pseudo-element        | Description                          |
|:----------------------|:-------------------------------------|
| ::first-letter        | 첫글자를 선택한다
| ::first-line          | 첫줄을 선택한다
| ::after               | 태그 뒤에 위치하는 공간을 선택한다
| ::before              | 태그 앞에 위치하는 공간을 선택한다
| ::selection           | 드래그한 글자를 선택한다

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      p::first-letter {
        font-size: 3em;
      }
      p::first-line {
        color: red;
      }

      h1::before {
        content: " HTML!!! ";
        color: blue;
      }
      h1::after {
        content: " CSS3!!!";
        color: red;
      }

      ::-moz-selection { /* Code for Firefox */
        color: red;
        background: yellow;
      }
      ::selection {
        color: red;
        background: yellow;
      }
    </style>
  </head>
  <body>
    <h1>This is a heading</h1>
    <p>You can use the ::first-line pseudo-element to add a special effect to the first line of a text. Some more text. And even more, and more, and more, and more, and more, and more, and more, and more, and more, and more, and more, and more.</p>
  </body>
</html>
```

# 2. CSS 적용 우선 순위 (Cascading Order)

기본적으로 선언된 순서에 따라 우선 순위가 적용된다. 즉, 나중에 선언된 스타일이 우선 적용된다.

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      p { color: blue; }
      p { color: red; }
    </style>
  </head>
  <body>
    <p>Will be RED.</p>
  </body>
</html>  
```

그러나 스타일 적용 방법이나 선택자에 따라 우선순위가 적용된다.

```
!important > 인라인 스타일 > 아이디 선택자 > 클래스/속성/가상 선택자 > 태그 선택자 > 전체 선택자 > 상위 객체에 의해 상속된 속성
```

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      p {
        color: red !important;
      }
      #thing {
        color: blue;
      }
      .food {
        color: green;
      }
      div {
        color: orange;
      }
    </style>
  </head>
  <body>
    <p id="thing">Will be Red.</p>
    <div class="food">Will be Green.</div>
  </body>
</html>
```

또한 연동 방식에 따라서도 우선순위가 적용된다.

1. `<head>` 요소 내 style 요소
2. `<style>` 요소 내 @import 문
3. `<link>` 로 연결된 CSS 파일
4. `<link>` 로 연결된 CSS 파일 내의 @import 문
5. 브라우저 디폴트 스타일시트

```html
<!DOCTYPE html>
<html>
  <head>
    <link rel="stylesheet" type="text/css" href="mystyle.css">
    <style>
      body {
        background-color: yellow;
        color: navy;
      }
    </style>
  </head>
  <body style="background-color: beige">
    <h1>Multiple Styles Will Cascade into One</h1>
    <p>In this example, the background color is set inline, in an internal stylesheet, and in an external stylesheet.</p>
    <p>Try experimenting by removing styles to see how the cascading stylesheets work. (try removing the inline first, then the internal, then the external)</p>
  </body>
</html>
```

```css
body {
  background-color: blue;
  color: red;
}
```

# 3. CSS 속성값(Property Values)의 표현

CSS 속성값은 키워드, 크기 단위, 색상 표현 단위 등의 특정 단위를 갖는다.

## 3.1 키워드

각 속성에 따라 별도의 키워드가 존재한다. 자세한 내용은 [CSS 속성](/css/CSS3-Basics/#css-property)에서 설명하기로 한다.

## 3.2 크기 단위

cm, mm, inch 등의 단위도 존재하나 대표적인 크기 단위는 다음과 같다. px은 절대값이고 em, %는 상재값이 된다.

| 단위        | Description                          |
|:-----------|:-------------------------------------|
| px         | 픽셀 단위 (1px = 1/96 inches)
| em         | 배수 단위 (2em은 2배의 크기를 의미한다)
| %          | 백분률 단위

속성값이 0인 경우, 단위를 지정하지 않아도 된다.

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      #px > :nth-child(1) { }
      #px > :nth-child(2) { font-size: 16px; }
      #px > :nth-child(3) { font-size: 24px; }
      #px > :nth-child(4) { font-size: 32px; }

      #em > :nth-child(1) { }
      #em > :nth-child(2) { font-size: 1.0em; }
      #em > :nth-child(3) { font-size: 1.5em; }
      #em > :nth-child(4) { font-size: 2.0em; }

      #percent > :nth-child(1) { }
      #percent > :nth-child(2) { font-size: 100%; }
      #percent > :nth-child(3) { font-size: 150%; }
      #percent > :nth-child(4) { font-size: 200%; }
    </style>
  </head>
  <body>
    <h1>px uint</h1>
    <div id="px">
      <p>This is a paragraph</p>
      <p>This is a paragraph</p>
      <p>This is a paragraph</p>
      <p>This is a paragraph</p>
    </div>

    <h1>em unit</h1>
    <div id="em">
      <p>This is a paragraph</p>
      <p>This is a paragraph</p>
      <p>This is a paragraph</p>
      <p>This is a paragraph</p>
    </div>

    <h1>% unit</h1>
    <div id="percent">
      <p>This is a paragraph</p>
      <p>This is a paragraph</p>
      <p>This is a paragraph</p>
      <p>This is a paragraph</p>
    </div>
  </body>
</html>
```

## 3.3 색상 표현 단위

색상을 지정하기 위해 키워드(red, blue...)를 사용할 수 있다. 사용이 간편하다는 장점이 있으나 표현할 수 있는 색상의 수는 제한된다.

색상를 표현할 수 있는 키워드 리스트는 [W3C css3-color ](https://www.w3.org/TR/css3-color/) 를 참고하기 바란다.

```html
<!DOCTYPE html>
<html>
  <body>
    <h2 style="background-color:red">
    Red background-color
    </h2>

    <h2 style="background-color:green">
    Green background-color
    </h2>

    <h2 style="background-color:blue;color:white">
    Blue background-color and white text color
    </h2>

    <h2 style="background-color:orange">
    Orange background-color
    </h2>

    <h2 style="background-color:yellow">
    Yellow background-color
    </h2>

    <h2 style="background-color:cyan">
    Cyan background-color
    </h2>

    <h2 style="background-color:black;color:white">
    Black background-color and white text color
    </h2>
  </body>
</html>
```

더욱 다양한 색상을 표현하기 위해 다음과 같은 색상 표현 단위를 사용할 수 있다.

| 단위                               | 사용예                          |
|:----------------------------------|:------------------------------|
| HEX 코드 단위 (Hexadecimal Colors)  | #000000
| RGB (Red, Green, Blue)            | rgb(255, 255, 0)
| RGBA (Red, Green, Blue, Alpha)    | rgba(255, 255, 0, 1)
| HSL                               | hsl(0, 100%, 25%)
| HSLA                              | hsla(60, 100%, 50%, 1)

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      #hex-p1 {background-color:#ff0000;}
      #hex-p2 {background-color:#00ff00;}
      #hex-p3 {background-color:#0000ff;}
      #hex-p4 {background-color:#ffff00;}
      #hex-p5 {background-color:#ff00ff;}

      #rgb-p1 {background-color:rgb(255,0,0);}
      #rgb-p2 {background-color:rgb(0,255,0);}
      #rgb-p3 {background-color:rgb(0,0,255);}
      #rgb-p4 {background-color:rgb(192,192,192);}
      #rgb-p5 {background-color:rgb(255,255,0);}
      #rgb-p6 {background-color:rgb(255,0,255);}

      #rgba-p1 {background-color:rgba(255,0,0,0.3);}
      #rgba-p2 {background-color:rgba(0,255,0,0.3);}
      #rgba-p3 {background-color:rgba(0,0,255,0.3);}
      #rgba-p4 {background-color:rgba(192,192,192,0.3);}
      #rgba-p5 {background-color:rgba(255,255,0,0.3);}
      #rgba-p6 {background-color:rgba(255,0,255,0.3);}

      #hsl-p1 {background-color:hsl(120,100%,50%);}
      #hsl-p2 {background-color:hsl(120,100%,75%);}
      #hsl-p3 {background-color:hsl(120,100%,25%);}
      #hsl-p4 {background-color:hsl(120,60%,70%);}
      #hsl-p5 {background-color:hsl(290,100%,50%);}
      #hsl-p6 {background-color:hsl(290,60%,70%);}

      #hsla-p1 {background-color:hsla(120,100%,50%,0.3);}
      #hsla-p2 {background-color:hsla(120,100%,75%,0.3);}
      #hsla-p3 {background-color:hsla(120,100%,25%,0.3);}
      #hsla-p4 {background-color:hsla(120,60%,70%,0.3);}
      #hsla-p5 {background-color:hsla(290,100%,50%,0.3);}
      #hsla-p6 {background-color:hsla(290,60%,70%,0.3);}
    </style>
  </head>

  <body>
    <h1>HEX colors:</h1>
    <p id="hex-p1">Red</p>
    <p id="hex-p2">Green</p>
    <p id="hex-p3">Blue</p>
    <p id="hex-p4">Yellow</p>
    <p id="hex-p5">Cerise</p>

    <h1>RGB colors:</h1>
    <p id="rgb-p1">Red</p>
    <p id="rgb-p2">Green</p>
    <p id="rgb-p3">Blue</p>
    <p id="rgb-p4">Grey</p>
    <p id="rgb-p5">Yellow</p>
    <p id="rgb-p6">Cerise</p>

    <h1>RGB colors with opacity:</h1>
    <p id="rgba-p1">Red</p>
    <p id="rgba-p2">Green</p>
    <p id="rgba-p3">Blue</p>
    <p id="rgba-p4">Grey</p>
    <p id="rgba-p5">Yellow</p>
    <p id="rgba-p6">Cerise</p>

    <h1>HSL colors:</h1>
    <p id="hsl-p1">Green</p>
    <p id="hsl-p2">Light green</p>
    <p id="hsl-p3">Dark green</p>
    <p id="hsl-p4">Pastel green</p>
    <p id="hsl-p5">Violet</p>
    <p id="hsl-p6">Pastel violet</p>

    <h1>HSL colors with opacity:</h1>
    <p id="hsla-p1">Green</p>
    <p id="hsla-p2">Light green</p>
    <p id="hsla-p3">Dark green</p>
    <p id="hsla-p4">Pastel green</p>
    <p id="hsla-p5">Violet</p>
    <p id="hsla-p6">Pastel violet</p>
  </body>
</html>
```

# 4. CSS 속성(Property)

## 4.1 block / inline

모든 HTML 요소는 아무런 CSS를 적용하지 않아도 기본적으로 브라우저에 표현되는 디폴트 표시 값을 가진다. 대부분의 HTML 요소는 block 또는 inline 속성을 갖는다.

아래는 p 요소에 대한 크롬 브라우저의 디폴트 css이다.

```css
p {
  display: block;
  -webkit-margin-before: 1em;
  -webkit-margin-after: 1em;
  -webkit-margin-start: 0px;
  -webkit-margin-end: 0px;
}
```

### 4.1.1 block 속성

- 항상 새로운 라인에서 시작한다.

- 화면 크기 전체의 가로폭을 차지한다. (width: 100%)

- width, height, margin 속성 지정이 가능하다.

- block 요소 예

  - div

  - h1 ~ h6

  - p

  - ol

  - ul

  - li

  - hr

  - table

  - form

  ```html
  <!DOCTYPE html>
  <html>
    <body>
      <div style="background-color:black; color:white; padding:20px;">
        <h2>London</h2>
        <p>London is the capital city of England. It is the most populous city in the United Kingdom, with a metropolitan area of over 13 million inhabitants.</p>
      </div>
      <div style="background-color:red; color:white; padding:20px; width:200px;">
        <h2>Paris</h2>
        <p>Paris is the capital and most populous city of France. Situated on the Seine River, in the north of the country.</p>
      </div>
    </body>
  </html>
  ```

### 4.1.2 inline 속성

- 새로운 라인에서 시작하지 않으며 문장의 중간에 들어갈 수 있다. 즉, 줄을 바꾸지 않고 다른 요소와 함께 한 행에 위치시킬 수 있다.

- content의 폭만큼만 가로폭을 차지한다.

- width, height, margin-top, margin-bottom 속성 지정이 불가능하다. inline 요소를 연속 사용하는 경우, 간격을 유지하기 위해서 좌, 우에 약 5px 가량의 외부 여백(margin)이 자동 지정된다. 그리고 inline 요소의 상, 하 여백은 line-height 속성으로 지정한다.

- inline 요소 예

  - span

  - a

  - strong

  - img

  - br

  - input

  - select

  - textarea

  - button

```html
<!DOCTYPE html>
<html>
  <body>
    <h1>My <span style="background-color:red; color:white;">Important</span> Heading</h1>
  </body>
</html>
```

### 4.1.3 inline-block 요소

block과 inline의 특징을 모두 갖는다. inline 요소 같이 한 줄에 표현되면서 width, height, margin 속성을 지정할 수 있다. 디폴트 표시값으로 inline-block 속성을 갖는 요소는 없다. inline-block 속성을 갖게 하려면 별도 지정이 필요하다.

- 기본적으로 inline 속성과 흡사하게 줄을 바꾸지 않고 다른 요소와 함께 한 행에 위치시킬 수 있다.

- block 속성처럼 width와 height, margin 속성을 정의할 수 있다. 상, 하 여백을 margin과 line-height 두가지 속성 모두를 통해 제어할 수 있다.

- inline-block 속성을 가진 태그끼리 연속으로 사용되는 경우에는 최소한의 간격을 유지하기 위해서 좌, 우에 약 5px 가량의 외부 여백(margin)이 자동 지정된다. margin-left나 margin-right를 사용하면 추가로 여백을 지정 가능하다.

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      .floating-box {
        display: inline-block;
        width: 150px;
        height: 75px;
        margin: 10px;
        border: 3px solid #73AD21;
      }

      .after-box {
        border: 3px solid red;
      }
    </style>
  </head>
  <body>
    <div class="floating-box">Floating box</div>
    <div class="floating-box">Floating box</div>
    <div class="floating-box">Floating box</div>
    <div class="floating-box">Floating box</div>
    <div class="floating-box">Floating box</div>
    <div class="floating-box">Floating box</div>
    <div class="floating-box">Floating box</div>
    <div class="floating-box">Floating box</div>

    <div class="after-box">Another box, after the floating boxes...</div>
  </body>
</html>
```

## 4.2 표시 （Display）

### 4.2.1 display 속성

display 속성은 layout을 정의하기 위한 가장 중요한 CSS 속성이다.


| 속성값 키워드   | 설명                         |
|:-------------|:----------------------------|
| block        | block 속성 요소로 지정
| inline       | inline 속성 요소로 지정
| inline-block | inline-block 속성 요소로 지정
| none         | 해당 요소를 화면에 표시하지 않는다 (공간조차 사라진다)

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      span {
        display: block;
        width: 150px;
        height: 75px;
        margin: 10px;
        border: 3px solid #73AD21;
      }
      li {
        display: inline;
      }
      div {
        display: inline-block;
        width: 150px;
        height: 75px;
        margin: 10px;
        border: 3px solid #73AD21;
      }
      .hidden {
        display: none;
      }
    </style>
  </head>
  <body>
    <h1>display: block</h1>

    <span>A display property with a value of "block" results in</span> <span>a line break between the two elements.</span>

    <h1>display: inline</h1>

    <ul>
      <li><a href="/html/default.asp" target="_blank">HTML</a></li>
      <li><a href="/css/default.asp" target="_blank">CSS</a></li>
      <li><a href="/js/default.asp" target="_blank">JavaScript</a></li>
    </ul>

    <h1>display: inline-block</h1>

    <div>This is a div</div>
    <strong>This is a strong</strong>

    <h1>display: none</h1>

    <h1 class="hidden">This is a hidden heading</h1>
    <p>Notice that the h1 element with display: none; does not take up any space.</p>
  </body>
</html>
```

### 4.2.2 visibility 속성

visibility 속성은 요소를 보이게 할 것인지 보이지 않게 할 것인지를 정의한다.

| 속성값 키워드   | 설명                         |
|:-------------|:----------------------------|
| visible      | 해당 요소를 보이게 한다 (기본값)
| hidden       | 해당 요소를 보이지 않게 한다. display 속성의 none 속성값과 다르게 해당 공간은 사라지지 않는다.
| collapse     | inline-block 속성 요소로 지정
| none         | 테이블 요소의 row나 column을 보이지 않게 한다. IE, 파이어폭스에서만 동작하며 크롬에서는 hidden과 동일하게 동작한다.

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      h1.visible {
        visibility: visible
      }
      h1.hidden {
        visibility: hidden
      }

      table, td {
        border: 1px solid black;
      }
      tr.collapse {
        visibility: collapse;
      }
    </style>
  </head>
  <body>
    <h1 class="visible">This is a visible heading</h1>
    <h1 class="hidden">This is an invisible heading</h1>

    <table>
      <tr>
        <td>Peter</td>
        <td>Griffin</td>
      </tr>
      <tr class="collapse">
        <td>Lois</td>
        <td>Griffin</td>
      </tr>
    </table>
  </body>
</html>
```

### 4.2.3 opacity 속성

opacity 속성은 요소의 투명도를 정의한다. 0.0 ~ 1.0의 값을 입력하며 0.0은 투명, 1.0은 불투명을 의미한다.

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      div, img {
        background-color: blue;
        color: white;

        opacity: 0.5;
        filter: Alpha(opacity=50); /* IE8 and earlier */
      }

      div:hover, img:hover {
        opacity: 1.0;
        filter: alpha(opacity=100); /* For IE8 and earlier */
      }
    </style>
  </head>
    <body>
    <div>This element's opacity is 0.5! Note that both the text and the background-color are affected by the opacity level!</div>

    <h1>Image Transparency</h1>
    <img src="klematis.jpg" width="150" height="113" alt="klematis">
  </body>
</html>
```

## 4.3 박스 모델 (Box Model)

모든 HTML 요소는 박스 형태의 영역을 가지고 있다.

![typesetting](/img/typesetting.jpg)

CSS 박스 모델은 모든 HTML 요소를 감싸고 있는 margin, border, padding 속성을 의미한다.

![css box model](/img/box-model.png)

| 명칭     | 설명
|:--------|:-----------------------------------------------------------
| Content | 요소의 텍스트나 이미지 등의 내용이 위치하는 영역이다. width, height 속성을 갖는다.
| Padding | 테두리 내부 영역이다. 속성값은 두께를 의미하며 기본적으로 투명한 색을 갖는다.
| Border  | 테두리 영역이다. 속성값은 두께를 의미한다.
| Margin  | 테두리의 외부 영역이다. 기본적으로 투명한 색을 갖는다.

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      div {
        background-color: lightgrey;
        width: 300px;
        padding: 25px;
        border: 25px solid navy;
        margin: 25px;
      }
    </style>
  </head>
  <body>
    <h2>Demonstrating the Box Model</h2>

    <div>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</div>
  </body>
</html>
```

### 4.3.1 width / height 속성

width와 height 속성은 요소의 내용(content)가 위치하는 영역의 너비와 높이를 의미한다. 따라서 박스 전체 크기는 다음과 같이 계산할 수 있다.

- 전체 너비 = width + left padding + right padding + left border + right border + left margin + right margin

- 전체 높이 = height + top padding + bottom padding + top border + bottom border + top margin + bottom margin

### 4.3.2 margin / padding 속성

margin / padding 속성은 content의 4개 방향에 대하여 지정이 가능하다.

![box model detail](/img/box-model-detail.png)

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      div {
        border:5px solid red;

        margin-top: 40px;
        margin-right: 30px;
        margin-bottom: 20px;
        margin-left: 10px;

        padding-top: 10px;
        padding-right: 20px;
        padding-bottom: 30px;
        padding-left: 40px;
      }
    </style>
  </head>
  <body>
    <div>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</div>
  </body>
</html>
```

-top, -right, -bottom, -left 4방향의 속성을 각각 지정하지 않고 margin, padding 1개의 속성만으로 4방향의 속성을 한번에 지정할 수 있다.

- 4개의 값을 지정할 때
  - margin: 25px 50px 75px 100px;
    - top margin : 25px
    - right margin : 50px
    - bottom margin : 75px
    - left margin : 100px

- 3개의 값을 지정할 때
  - margin: 25px 50px 75px;
    - top margin : 25px
    - right, left margin : 50px
    - bottom margin : 75px

- 2개의 값을 지정할 때
  - margin: 25px 50px;
    - top, bottom margin : 25px
    - right, left margin : 50px

- 1개의 값을 지정할 때
  - margin: 25px;
    - top, right, bottom, left margin : 25px


```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      div {
        border:5px solid red;

        margin:  40px 30px 20px 10px;
        padding: 10px 20px 30px 40px;
      }
    </style>
  </head>
  <body>
    <div>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</div>
  </body>
</html>
```

margin 속성에 `auto` 키워드를 설정하면 해당 요소를 브라우저 중앙에 위치 시킬 수 있다.

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      div {
        border:5px solid red;
        width: 600px;
        margin: auto;
      }
    </style>
  </head>
  <body>
    <div>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</div>
  </body>
</html>
```

브라우저 너비가 요소 너비보다 좁으면 가로 스크롤바가 만들어진다. 이 문제를 해결하기 위해서 `max-width` 속성을 사용할 수 있다.

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      div {
        border:5px solid red;
        max-width: 600px;
        margin: auto;
      }
    </style>
  </head>
  <body>
    <div>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</div>
  </body>
</html>
```

`max-width` 속성을 사용하면 브라우저 너비가 요소의 너비보다 좁아질 때 자동으로 요소의 너비가 줄어든다.

### 4.3.3 border 속성

Border Style

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      p.dotted { border-style: dotted; }
      p.dashed { border-style: dashed; }
      p.solid  { border-style: solid; }
      p.double { border-style: double; }
      p.groove { border-style: groove; }
      p.ridge  { border-style: ridge; }
      p.inset  { border-style: inset; }
      p.outset { border-style: outset; }
      p.none   { border-style: none; }
      p.hidden { border-style: hidden; }
      p.mix    { border-style: dotted dashed solid double; }
    </style>
  </head>
  <body>
    <h2>The border-style Property</h2>
    <p>This property specifies what kind of border to display:</p>

    <p class="dotted">A dotted border.</p>
    <p class="dashed">A dashed border.</p>
    <p class="solid">A solid border.</p>
    <p class="double">A double border.</p>
    <p class="groove">A groove border.</p>
    <p class="ridge">A ridge border.</p>
    <p class="inset">An inset border.</p>
    <p class="outset">An outset border.</p>
    <p class="none">No border.</p>
    <p class="hidden">A hidden border.</p>
    <p class="mix">A mixed border.</p>
  </body>
</html>
```

Border Width

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      p.one {
        border-style: solid;
        border-width: 5px;
      }
      p.two {
        border-style: solid;
        border-width: medium;
      }
      p.three {
        border-style: dotted;
        border-width: 2px;
      }
      p.four {
        border-style: dotted;
        border-width: thick;
      }
      p.five {
        border-style: double;
        border-width: 15px;
      }
      p.six {
        border-style: double;
        border-width: thick;
      }
      p.seven {
        border-style: solid;
        border-width: 2px 10px 4px 20px;
      }
    </style>
  </head>
  <body>
    <h2>The border-width Property</h2>
    <p>This property specifies the width of the four borders:</p>

    <p class="one">Some text.</p>
    <p class="two">Some text.</p>
    <p class="three">Some text.</p>
    <p class="four">Some text.</p>
    <p class="five">Some text.</p>
    <p class="six">Some text.</p>
    <p class="seven">Some text.</p>

    <p><b>Note:</b> The "border-width" property does not work if it is used alone.
    Always specify the "border-style" property to set the borders first.</p>
  </body>
</html>
```

Border Color

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      p.one {
        border-style: solid;
        border-color: red;
      }
      p.two {
        border-style: solid;
        border-color: green;
      }
      p.three {
        border-style: solid;
        border-color: red green blue yellow;
      }
    </style>
  </head>
  <body>
    <h2>The border-color Property</h2>
    <p>This property specifies the color of the four borders:</p>

    <p class="one">A solid red border</p>
    <p class="two">A solid green border</p>
    <p class="three">A solid multicolor border</p>
    <p><b>Note:</b> The "border-color" property does not work if it is used alone. Use the "border-style" property to set the borders first.</p>
  </body>
</html>
```

Border Radius

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      div {
        background: #eaeaed;
        color: #666;
        display: inline-block;
        width: 90px;
        height: 90px;
        line-height: 90px;
        margin: 0 14px;
        text-align: center;
      }

      .border-rounded {
        border-radius: 5px;
      }
      .border-circle {
        border-radius: 50%;
      }
      .border-football {
        border-radius: 15px 75px;
      }
    </style>
  </head>
  <body>
    <div class="border-rounded">5px</div>
    <div class="border-circle">50%</div>
    <div class="border-football">15px 75px</div>
  </body>
</html>
```

### 4.3.4 box-sizing 속성

| 키워드           | 설명
|:----------------|:-----------------------------------------------------------
| content-box     | width, height 속성값은 content 영역을 의미한다. (기본값)
| border-box      | width, height 속성값은 content 영역, padding, border가 포함된 값을 의미한다.

![box-sizing](/img/box-sizing.png)

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      .content-box {
        width: 600px;
        border: 10px solid;
        padding: 50px;
        margin: 50px;
        background-color: red;
      }
      .border-box {
        box-sizing: border-box;
        width: 600px;
        border: 10px solid;
        padding: 50px;
        margin: 50px;
        background-color: red;
      }
    </style>
  </head>
  <body>
  <div class="content-box">content-box</div>
  <div class="border-box">border-box</div>
</body>
</html>
```

## 4.4 배경 (Background)

해당 요소의 배경으로 이미지 또는 색상을 정의한다.

### 4.4.1 Background Image

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      body {
        background-image: url("dot.png");
      }
      </style>
  </head>
  <body>
    <h1>Hello World!</h1>
    <p>This page has an image as the background!</p>
  </body>
</html>
```

background-image에 복수개의 이미지를 설정할 경우, 먼저 설정된 이미지가 전면에 출력된다.

```css
background-image: url("front.png"), url("back.png");
```

설정된 이미지의 크기가 화면보다 작으면 자동으로 이미지가 반복 출력되어 화면을 채우게 된다. 이것은 `background-repeat` 속성의 기본값이 `repeat`이기 때문이다.

x축으로만 배경 이미지를 반복할 경우, `background-repeat` 속성값에 `repeat-x`, y축으로만 배경 이미지를 반복할 경우, `repeat-y`를 설정한다.

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      body {
        background-image: url("dot.png");
        background-repeat: repeat-x;
      }
      </style>
  </head>
  <body>
    <h1>Hello World!</h1>
    <p>This page has an image as the background!</p>
  </body>
</html>
```

반복 출력을 멈추고 싶은 경우, `background-repeat` 속성값에 `no-repeat`를 설정한다.

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      body {
        background-image: url("dot.png");
        background-repeat: no-repeat;
      }
      </style>
  </head>
  <body>
    <h1>Hello World!</h1>
    <p>This page has an image as the background!</p>
  </body>
</html>
```

배경 이미지의 크기를 조절하고 싶은 경우, `background-size` 속성을 사용한다. px값을 지정할 경우, 배경이미지 크기가 지정된 px값으로 조정되고 100%를 지정하며 화면 크기에 맞추어 이미지를 출력한다. 이때 지정한 값은 width를 의미한다.

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      body {
        background-image: url("dot.png");
        background-repeat: no-repeat;
        background-size: 100%;
      }
      </style>
  </head>
  <body>
    <h1>Hello World!</h1>
    <p>This page has an image as the background!</p>
  </body>
</html>
```

배경이미지의 width, height를 모두 설정할 수 있다. 이때 첫번째 값은 width, 두번째 값은 height를 의미한다.

```html
background-size: 100% 500px;
```

이때 쉼표로 값을 구분하면 다른 배경이미지의 너비를 지정하는 것으로 인식된다.

```html
background-image: url("front.png"), url("back.png");
background-size: 100%, 500px;
```

화면을 스크롤하면 배경 이미지도 함께 스크롤된다. 화면이 스크롤되더라도 배경이미지는 스크롤되지 않고 고정되어 있게 하려면 `background-attachment` 속성에 `fixed` 키워드를 지정한다.

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    div {
      background-image: url("background.jpg");
      background-size: 100% 100%;
      display: inline-block;
      width: 45%;
    }
    .fixed {
      background-attachment: fixed;
    }
  </style>
</head>
<body>

  <div>
    <p>The background-image is fixed. Try to scroll down the page.</p>
    <p>The background-image is fixed. Try to scroll down the page.</p>
    <p>The background-image is fixed. Try to scroll down the page.</p>
    <p>The background-image is fixed. Try to scroll down the page.</p>
    <p>The background-image is fixed. Try to scroll down the page.</p>
    <p>The background-image is fixed. Try to scroll down the page.</p>
    <p>The background-image is fixed. Try to scroll down the page.</p>
    <p>The background-image is fixed. Try to scroll down the page.</p>
    <p>The background-image is fixed. Try to scroll down the page.</p>
    <p>The background-image is fixed. Try to scroll down the page.</p>
    <p>The background-image is fixed. Try to scroll down the page.</p>
    <p>The background-image is fixed. Try to scroll down the page.</p>
    <p>The background-image is fixed. Try to scroll down the page.</p>
    <p>The background-image is fixed. Try to scroll down the page.</p>
    <p>The background-image is fixed. Try to scroll down the page.</p>
  </div>
  <div class='fixed'>
    <p>The background-image is fixed. Try to scroll down the page.</p>
    <p>The background-image is fixed. Try to scroll down the page.</p>
    <p>The background-image is fixed. Try to scroll down the page.</p>
    <p>The background-image is fixed. Try to scroll down the page.</p>
    <p>The background-image is fixed. Try to scroll down the page.</p>
    <p>The background-image is fixed. Try to scroll down the page.</p>
    <p>The background-image is fixed. Try to scroll down the page.</p>
    <p>The background-image is fixed. Try to scroll down the page.</p>
    <p>The background-image is fixed. Try to scroll down the page.</p>
    <p>The background-image is fixed. Try to scroll down the page.</p>
    <p>The background-image is fixed. Try to scroll down the page.</p>
    <p>The background-image is fixed. Try to scroll down the page.</p>
    <p>The background-image is fixed. Try to scroll down the page.</p>
    <p>The background-image is fixed. Try to scroll down the page.</p>
    <p>The background-image is fixed. Try to scroll down the page.</p>
  </div>
</body>
</html>
```

### 4.4.2 Background Position

| 속성값	        | Description
|:--------------|:-----------------
| left top       | x축 y축
| left center    | x축 y축
| left bottom    | x축 y축
| right top      | x축 y축
| right center   | x축 y축
| right bottom   | x축 y축
| center top     | x축 y축
| center center  | x축 y축
| center         | center center
| bottom	       | bottom center
| x% y%          | x축 y축
| xpos ypos      | x축 y축

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      div {
        background-image: url('dot.png');
        background-repeat: no-repeat;
        background-attachment: fixed;
        background-position: center;
      }
    </style>
  </head>
  <body><div></div></body>
</html>
```

### 4.4.3 Background Color

```css
div {
  background-color:red;
  background-color:rgb(255,255,255);
}
```

## 4.5 폰트와 텍스트

폰트 및 텍스트 관련 속성은 폰트의 크기, 폰트의 지정, 폰트의 스타일, 텍스트 정렬 등을 정의한다.

### 4.5.1 font-size 속성

텍스트의 크기를 정의한다.

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      .font-size-40 { font-size: 40px; }
      .font-size-2x { font-size: 2.0em; }
      .font-size-150ps { font-size: 150%; }
      .font-size-large { font-size: large; }

    </style>
  </head>
  <body>
    <p>This is text: p tag's default font size: 16px</p>
    <p class='font-size-40'>This is text</p>
    <p class='font-size-2x'>This is text</p>
    <p class='font-size-150ps'>This is text</p>
    <p class='font-size-large'>This is text</p>
  </body>
</html>
```

### 4.5.2 font-family 속성

폰트를 지정한다. 컴퓨터에 폰트가 설치되어 있지 않으면 적용되지 않는다. 폰트는 복수개 지정이 가능한데 첫번째 지정한 폰트가 클라이언트 컴퓨터에 설치되어 있지 않은 경우, 다음에 지정된 폰트를 적용한다. 따라서 마지막에 지정하는 폰트는 대부분의 OS에 기본적으로 설치되어 있는 generic-family 폰트(Serif, Sans-serif, Mono space)를 지정하는 것이 일반적이다.

다음은 맥용 크롬 브라우저의 generic-family 폰트 설정 화면이다.

![Chrome generic-family font](/img/generic-family-font.png)

폰트명은 따옴표로 감싸주며 폰트명이 한단어인 경우는 따옴표로 감싸주지 않아도 된다.

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      p.serif {
        font-family: "Times New Roman", Times, serif;
      }

      p.sansserif {
        font-family: Arial, Helvetica, sans-serif;
      }
    </style>
  </head>
  <body>
    <h1>CSS font-family</h1>
    <p class="serif">This is a paragraph, shown in the Times New Roman font.</p>
    <p class="sansserif">This is a paragraph, shown in the Arial font.</p>
  </body>
</html>
```

### 4.5.2 font-style / font-weight 속성

font-style 속성은 이탤릭체의 지정, font-weight 속성은 폰트 굵기 지정에 사용된다.

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      p { font-size: 2.0em; }

      /* font-style */
      .italic {
        font-style: italic;
      }

      /* font-weight */
      .light {
        font-weight: lighter;
      }
      .thick {
        font-weight: bold;
      }
      .thicker {
        font-weight: 900;
      }
    </style>
  </head>
  <body>
    <p>normal style.</p>
    <p class="italic">font-style: italic</p>

    <p class="light">font-weight: lighter</p>
    <p class="thick">font-weight: bold</p>
    <p class="thicker">font-weight: 900</p>
  </body>
</html>
```

### 4.5.3 line-height 속성

텍스트의 높이를 지정한다. 텍스트 수직 정렬에도 응용되어 사용된다.

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      .small {
        line-height: 70%;
      }
      .big {
        line-height: 200%;
      }
    </style>
  </head>
  <body>
    <p>
    This is a paragraph with a standard line-height.<br>
    This is a paragraph with a standard line-height.<br>
    The default line height in most browsers is about 110% to 120%.<br>
    </p>

    <p class="small">
      This is a paragraph with a smaller line-height.<br>
      This is a paragraph with a smaller line-height.<br>
    </p>

    <p class="big">
      This is a paragraph with a bigger line-height.<br>
      This is a paragraph with a bigger line-height.<br>
    </p>
  </body>
</html>
```

다음은 수직 중앙 정렬 예제이다. a 요소의 `line-height` 값과 a 요소를 감싸는　div 요소의 `height` 값을 일치시킨다.

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      .button {
        width: 150px;
        height: 70px;
        background-color: #FF6A00;
        border: 10px solid #FFFFFF;
        border-radius: 30px;
        box-shadow: 5px 5px 5px #A9A9A9;
      }
      .button > a {
        display: block;
        font-size: 2em;
        font-style: italic;
        font-weight: bold;
        text-align: center;
        text-decoration: none;
        line-height: 70px;
      }
    </style>
  </head>
  <body>
    <div class="button">
      <a href="#">Click</a>
    </div>
  </body>
</html>
```

### 4.5.4 text-align 속성

텍스트의 수평 정렬을 정의한다.

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      h1 {
        text-align: center;
      }
      h3 {
        text-align: right;
      }
      p {
        text-align: left;
      }
      a {
        text-align: center;
      }
    </style>
  </head>
  <body>
    <h1>Understanding Node.js</h1>
    <h3>2016.03.07</h3>
    <p>As developers, we often face situations where we need to use unfamiliar code. A question will arise during these moments. How much time should I invest in understanding the code that I’m about to use? A typical answer is learn enough to start coding; then explore that topic further when time permits. Well, the time has come to gain a better understanding of module.exports and exports in Node.js. Here’s what I have learned.</p>

    <a href='#'>Reference</a>
  </body>
</html>
```

위 예제의 a 요소에 대한 중앙 정렬은 적용되지 않았다. 이는 a 요소는 inline 요소이기 때문이다. inline 요소는 width 속성이 없으므로 중앙 개념이 존재하지 않는다. a 요소에 `display: block;`을 지정한다면 중앙 정렬이 가능할 것이다.

### 4.5.5 text-decoration 속성

text-decoration 속성을 사용하여 링크 underline을 제거할 수 있다. 또는 텍스트에 underline, overline, line-through를 추가할 수도 있다.

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      a { text-decoration: none; }

      p:nth-of-type(1) { text-decoration: overline; }
      p:nth-of-type(2) { text-decoration: line-through; }
      p:nth-of-type(3) { text-decoration: underline; }
    </style>
  </head>
  <body>
    <a href='#'>text-decoration: none</a>

    <p>text-decoration: overline</p>
    <p>text-decoration: line-through</p>
    <p>text-decoration: underline</p>
  </body>
</html>
```

## 4.6 위치 (Position)

position

z-index

overflow





## 4.7 float

## 4.8 Shadow / Rounded Corner / Gradients


----->CSS3
## Transitions

## Animations

## Media Queries
----->CSS3



# 5. Layout

# 6. Responsive Web Design




# Reference

* [w3schools.com](http://www.w3schools.com)

* [Learn to Code HTML & CSS](http://learn.shayhowe.com/)

* [W3C CSS Document](https://www.w3.org/TR/CSS/)