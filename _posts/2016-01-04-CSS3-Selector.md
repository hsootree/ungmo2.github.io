---
layout: post
title: CSS3 Selector
categories: css
---

* TOC
{:toc}

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

# 1. 전체 선택자 (Universal Selector)

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

# 2. 태그 선택자 (Type Selector)

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

# 3. ID 선택자 (ID Selector)

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

# 4. 클래스 선택자 (Class Selector)

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

# 5. 속성 선택자 (Attribute Selector)

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

# 6. 복합 선택자 (Combinator)

## 6.1 후손 선택자 (Descendant Combinator)

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

## 6.2 자손 선택자 (Child Combinator)

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

## 6.3 동위 선택자

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

# 7. 가상 클래스 선택자 (Pseudo-Class Selector)

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

## 7.1 링크 선택자(Link pseudo-classes), 동적 선택자(User action pseudo-classes)

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

## 7.2 UI 요소 상태 선택자(UI element states pseudo-classes)

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

## 7.3 구조 가상 클래스 선택자(Structural pseudo-classes)

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

## 7.4 부정 선택자(Negation pseudo-class)

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

# 8. 가상 요소 선택자 (Pseudo-Element Selector)

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

# 9. CSS 적용 우선 순위 (Cascading Order)

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

# Reference

* [w3schools.com](http://www.w3schools.com)

* [Learn to Code HTML & CSS](http://learn.shayhowe.com/)

* [W3C CSS Document](https://www.w3.org/TR/CSS/)