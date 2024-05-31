# 3주차 정리

# 인터랙티브 JavaScript

## id로 태그 선택하기

```jsx
document.getElementById('id');
```

```jsx
const myTag1 = document.getElementById('myNumber');
console.log(myTag1);
```

- id 속성은 코드 전체에서 봤을 때 다른 태그들과 구분하기 위해 붙여주는 고유한 값
- id 속성을 통해서 어떤 요소를 가져오겠다는 의미
- 이 메소드의 파라미터로 접근하고자 하는 태그의 id 값을 문자열로 전달해주면 해당되는 태그가 선택된다.
- 해당 태그 내부의 모든 내용들이 표시된다.
- 존재하지 않는 태그는 null이 뜬다.

## class로 태그 선택하기

```jsx
document.getElementsByClassName('class');
```

```jsx
const myTags = document.getElementsByClassName('color-btn');
console.log(myTags);
```

- id는 고유한 값이기에 여러 elements를 선택하기엔 좋지 않다. 이때 class를 사용한다.
- 배열의 형태로 나오지만 완벽한 배열은 아니다. (유사배열) (splice, push 등 사용불가)
- `myTags[1], length, for문` 사용 가능
- 하나밖에 업는 class를 선택해도 요소 한 개가 들어있는 html 컬렉션이 출력된다.
- 존재하지 않는 class 값을 찾으면 `null`이 아니라 빈 html 컬렉션이 출력 된다.

## 유사 배열**(Array-Like Object)**이란?

- 배열과 모양은 같지만, 완벽히 배열은 아닌 형태이다.
- 유사 배열에도 최소한 갖춰야 할 조건과 특징들이 있다.
1. 숫자 형태의 indexing이 가능하다.
2. length 프로퍼티가 있다.
3. 배열의 기본 메소드를 사용할 수 없다.
4. Array.isArray(유사 배열)은 false다. (파라미터로 전달한 값이 배열인지 아닌지를 평가해서 그 결과를 불린 형태의 값으로 리턴해주는 메소드다.)

## 태그 이름으로 태그 선택하기

```jsx
document.getElementsByTagName('button');
```

```jsx
const btns = document.getElementsByClassName('color-btn');
const allTags = document.getElementsByTagName('*');
console.log(btns);
```

- HTML 문서 내에 있는 모든 `button` 태그를 선택하게 된다.
- 실행 결과로 class처럼 HTMLCollection을 리턴 한다.
- css 선택자처럼 `'*'` 값을 전달하게 되면 모든 태그를 선택할 수도 있다.

## css 선택자로 태그 선택하기

```jsx
document.querySelector('css');
```

```jsx
const myTag = document.querySelector('#myNumber');
console.log(myTag);

const myTag1 = document.querySelectorAll('.color-btn');
console.log(myTag1);
```

- css 선택자로 id를 선택할때는 #을 붙여 준다.
- All은 class처럼 여러 개를 선택하고 싶을때 사용한다.

## 이벤트와 버튼 클릭

```jsx
const btn = document.querySelector('#myBtn');
btn.onclick = function () {
  console.log("Hello Codeit!");
}
```

- 웹 페이지에서 일어날 수 있는 대부분의 일들을 이벤트라고 한다.
- 마우스를 움직이거나 페이지 스크롤, 마우스 클릭도 이벤트다.
- 이벤트가 발생했을 때 어떤 특정한 동작을 하도록 이벤트를 다루는 것을 이벤트 핸들링이라고 하고, 구체적인 동작을 코드로 표현한 함수 부분을 이벤트 핸들러라고 한다.
- html에서 직접 작성하기도 가능 (가독성 떨어지고, 코드의 일관성을 유지하기 어려워져서 잘 안 쓴다.)

## 브라우저도 객체인가?

- 자바스크립트는 원래 웹 브라우저를 다루기 위해 등장한 언어다.
- 자바스크립트는 모든 것이 객체다.
- 웹브라우저를 자바스크립트의 윈도우 객체로 다룰 수 있다.
- 윈도우 객체는 말 그대로 브라우저의 창을 대변한다. 객체 안의 프로퍼티를 활용하면 자바스크립트로 브라우저가 가지고 있는 다양한 정보를 얻거나 관리할 수 있다.
- 윈도우 객체는 브라우저의 창을 대변하면서 자바스크립트에서는 최상단에 존재하는 객체이다.
- 윈도우 객체는 자바스크립트의 어디서나 항상 접근할 수 있다. → 전역 객체

```jsx
console.log(window);
console.log(window.innerWidth); 
console.log(window.innerHeight);
-> 탭 내부의 너비와 높이를 얻을 수 있다.
```

```jsx
window.open ->새 창 열기
window.close -> 창 닫기
```

## DOM(Document Object Model / 문서 객체 모델)

- 웹 브라우저 안에 나타나는 컨텐츠 부분을 웹 페이지, 웹 문서라고도 표현한다.
- DOM은 웹 페이지에 나타나는 HTML 문서 전체를 객체로 표현한 것이다.
- Document 객체를 이용하면 웹페이지 내부를 맘대로 수정할 수 있고, 새로운 컨텐츠를 만들어 낼 수도 있다.

```jsx
console.log(document);
console.log(typeof document); // object
```

- DOM은 직접적으로 접근하게 되면 객체가 아니라 DOM에 해당하는 HTML이 출력된다.
- DOM을 태그가 아니라 객체로 보고 싶다면 아래를 사용하면 된다.

```jsx
console.dir(document);
```

- DOM 개념에 따르면 문서 내의 모든 태그들은 다 각각의 객체다.
- DOM을 사용하면 HTML 태그를 객체처럼 자유롭게 다룰 수 있다.

## `console.log`와 `console.dir` 차이?

### **1. 출력하는 자료형이 다르다.**

- dir 메소드는 문자열 표시 형식으로 콘솔에 출력한다.

### **2. log는 값 자체에, dir은 객체의 속성에!**

- `log` 메소드는 파라미터로 전달받은 값을 위주로 출력하는 반면, `dir` 메소드는 객체의 속성을 좀 더 자세하게 출력한다.

### **3. log는 여러 개, dir은 하나만!**

- `log` 메소드는 여러 값을 쉼표로 구분해서 전달하면 전달받은 모든 값을 출력하는 반면, `dir` 메소드는 여러 값을 전달하더라도 첫 번째 값만 ****출력한다.

### **4. DOM 객체를 다룰 때..**

- 값에 좀 더 중점을 둔 log 메소드는 대상을 HTML 형태로 출력하고, 객체의 속성에 좀 더 중점을 둔 dir 메소드는 대상을 객체 형태로 출력한다.

## DOM 트리

- DOM은 HTML문서를 객체화 한 것이기에 document 객체를 최상위로 해서 계층 구조를 이룬다.
- DOM 트리에서 각  개체를 노드라고 한다.
- 태그를 표현하는 노드를 요소 노드(element node)라고 한다.
- 문자를 표현하는 노드를 텍스트 노드(text node)라고 한다.
- 일반적으로 텍스트 노드들은 요소 노드의 자식 노드가 되고 스스로 자식을 가질 수 없다.

## DOM 트리에서 태그 선택하기

### **요소 노드에 대한 이동 프로퍼티**

```jsx
const myTag = document.querySelector('#list-1');
console.log(myTag);
```

```jsx
// 자식 요소 노드
console.log(myTag.children[1]);
console.log(myTag.firstElementChild); //자식들 중 첫번째 요소
console.log(myTag.lastElementChild);  //자식들 중 마지막 요소
```

```jsx
// 부모 요소 노드
console.log(myTag.parentElement)
```

```jsx
// 형제 요소 노드
console.log(myTag.previousElementSibling); //이전 혹은 좌측에 있는 요소
console.log(myTag.nextElementSibling);     // 다음 혹은 우측에 있는 요소
```

### **모든 노드에 대한 이동 프로퍼티**

```jsx
const myTag = document.querySelector('#list-1');
console.log(myTag);
```

```jsx
// 자식 요소 노드
node.childNodes
node.firstChild
node.lastChild	
```

```jsx
// 부모 요소 노드
node.parentNode	
```

```jsx
// 형제 요소 노드
node.previousSibling //이전 혹은 좌측에 있는 요소
node.nextSibling     // 다음 혹은 우측에 있는 요소
```

## 요소 노드 프로퍼티

```jsx
node.innerHTML;
node.innerHTML = '<li>Exotic</li>'; //해당 태그가 저걸로 완전히 변한다.
```

- 요소 안에 있는 문자열 HTML 자체를 문자열로 리턴해준다.
- 요소 안의 정보를 확인할 수도 있지만, 내부의 HTML 자체를 수정할 때 좀 더 자주 활용된다.
- 수정 시 내부에 있던 값을 완전히 새로운 값으로 교체한다.
- 줄바꿈이나 들여 쓰기도 다 표시된다.

```jsx
node.outerHTML;
node.outerHTML = '<li>Exotic</li>'; //요소 자체가 새로운 요소로 교체된다. (기존 요소는 사라진다.))
```

- 해당 요소를 포함한 전체 HTML 코드를 문자열로 리턴해준다.
- 줄바꿈이나 들여 쓰기도 다 표시된다.
- 새로운 값을 할당할 경우 요소 자체가 교체된다.

```jsx
node.textContent;
node.textContent = 'Exotic'; //해당 텍스트가 저걸로 완전히 변한다.
```

- 요소 안에 있는 내용들 중 HTML 태그 부분은 제외한 텍스트만 가져온다.
- 줄바꿈이나 들여 쓰기도 다 표시된다.
- 새로운 값을 할당하면 내부의 값을 완전히 새로운 값으로 교체 한다.
- 텍스트만 다루기 때문에, 특수문자도 그냥 텍스트로 처리한다.

### 요소 노드 추가하기

```jsx
// 1. 요소 노드 만들기 : document.creatElement('태그 이름')
const first = document.creatElement('li');

// 2. 요소 노드 꾸미기 : textContent, node.innerHTML
first.textContent = '처음';

// 3. 요소 노드 추가하기 : NODE.prepend, append, after, before
tomorrow.prepend(first);  // 메소드를 호출한 노드의 제일 첫번쨰 노드로 파라미터로 전달한 값을 맨 앞에  추가할 수 있다.
```

## 노드 삭제와 이동하기

```jsx
//  노드 삭제하기: Node.remove();
tomorrow.remove();
today.children[2].remove();
```

```jsx
// 노드 이동하기: prepend, append, before, after
today.append(tomorrow.children[1]);
tomorrow.children[1].after(today.children[1]);
```

## **HTML 속성 다루기**

- 대부분의 HTML 속성은 DOM 객체의 프로퍼티로 변환이 된다.
- 하지만, 표준 속성이 아닌 경우에는 프로퍼티로 변환이 안 되는데, 아래 메소드를 활용하면 표준이 아닌 HTML 속성들도 다룰 수 있다.

```jsx
// 1. 속성에 접근하기: 
element.getAttribute('속성')

// 2. 속성 추가(수정)하기:
element.setAttribute('속성', '값')
 
//3. 속성 제거하기: 
element.removeAttribute('속성')
```

## **스타일 다루기**

- 자바스크립트로 태그의 스타일을 다루는 방법에는 크게 두 가지가 있습니다.
1. style 프로퍼티 활용하기: 

`element.style.styleName = 'value';`

1. class 변경을 통해 간접적으로 스타일 적용하기:

 `element.className`, `element.classList`

### **classList의 유용한 메소드**

| 메소드 | 내용 | 참고사항 |
| --- | --- | --- |
| classList.add | 클래스 추가하기 | 여러 개의 값을 전달하면 여러 클래스 추가 가능 |
| classList.remove | 클래스 삭제하기 | 여러 개의 값을 전달하면 여러 클래스 삭제 가능 |
| classList.toggle | 클래스 없으면 추가, 있으면 삭제하기 | 하나의 값만 적용 가능하고,두 번째 파라미터로 추가 또는 삭제 기능을 강제할 수 있음 |

## 이벤트 핸들러 등록하기

```jsx
// 이벤트 등록하기
let btn = document.querySelector('#myBtn');

// btn.onclick = function () {
// 	console.log('Hi Codeit!');
// };
```

```jsx
function event1() {
	console.log('Hi Codeit!');
}

function event2() {
	console.log('Hi again!');
}

// elem.addEventListener(event 타입, handler)
btn.addEventListener('click', event1);
btn.addEventListener('click', event2);

// elem.removeEventListener(event 타입, handler(등록할 떄 저장했던 이벤트 핸들러))
btn.removeEventListener('click', event2);
```

- 이벤트 핸들러에 접근하는 2 가지 방법은 첫 번째는 DOM요소 에 접근한 다음 onclick 프로퍼티를 활용하는 방법이고, 두 번째는 HTML 태그에 onclick 속성을 활용하는 일이다.
- onclick방식도 새로운 이벤트 핸들러를 할당하면 기존의 값은 사라진다.

## 이벤트 객체

```jsx
// 이벤트 객체 (Event Object)
const myInput = document.querySelector('#myInput');
const myBtn = document.querySelector('#myBtn');

function printEvent(event) {
  console.log(event);
	event.target.style.color = 'red';
}

myInput.addEventListener('keydown', printEvent);
myBtn.addEventListener('click', printEvent);
```

- 이벤트와 관련된 다양한 정보를 담고 있는 이벤트 객체
- 이벤트 핸들러의 첫 번째 파라미터에는 이벤트 객체가 들어간다.

### **1. 공통 프로퍼티**

아래의 프로퍼티들은 이벤트 타입과 상관없이 모든 이벤트 객체들이 공통적으로 가지고 있는 프로퍼티다.

| 프로퍼티 | 설명 |
| --- | --- |
| type | 이벤트 이름 ('click', 'mouseup', 'keydown' 등) |
| target | 이벤트가 발생한 요소 |
| currentTarget | 이벤트 핸들러가 등록된 요소 |
| timeStamp | 이벤트 발생 시각(페이지가 로드된 이후부터 경과한 밀리초) |
| bubbles | 버블링 단계인지를 판단하는 값 |

### **2. 마우스 이벤트**

| 프로퍼티 | 설명 |
| --- | --- |
| button | 누른 마우스의 버튼 (0: 왼쪽, 1: 가운데(휠), 2: 오른쪽) |
| clientX, clientY | 마우스 커서의 브라우저 표시 영역에서의 위치 |
| pageX, pageY | 마우스 커서의 문서 영역에서의 위치 |
| offsetX, offsetY | 마우스 커서의 이벤트 발생한 요소에서의 위치 |
| screenX, screenY | 마우스 커서의 모니터 화면 영역에서의 위치 |
| altKey | 이벤트가 발생할 때 alt키를 눌렀는지 |
| ctrlKey | 이벤트가 발생할 때 ctrl키를 눌렀는지 |
| shiftKey | 이벤트가 발생할 때 shift키를 눌렀는지 |
| metaKey | 이벤트가 발생할 때 meta키를 눌렀는지 (window는 window키, mac은 cmd키) |

### **3. 키보드 이벤트**

| 프로퍼티 | 설명 |
| --- | --- |
| key | 누른 키가 가지고 있는 값 |
| code | 누른 키의 물리적인 위치 |
| altKey | 이벤트가 발생할 때 alt키를 눌렀는지 |
| ctrlKey | 이벤트가 발생할 때 ctrl키를 눌렀는지 |
| shiftKey | 이벤트가 발생할 때 shift키를 눌렀는지 |
| metaKey | 이벤트가 발생할 때 meta키를 눌렀는지 (window는 window키, mac은 cmd키) |

## **이벤트 버블링 (Event Bubbling)**

- 이벤트는 전파가 된다.
- 어떤 요소에서 이벤트가 발생하면 해당 요소에 등록된 이벤트 핸들러가 동작하는 것뿐만 아니라 부모 요소로 이벤트가 계속해서 전파되면서 각 요소에도 등록된 이벤트 핸들러가 있다면 차례로 이벤트 핸들러가 동작한다.
- 자식 요소에서 부모 요소로 이벤트가 전파되는 것을 이벤트 버블링(Event Bubbling)이라고 부릅니다.
- 참고로 이벤트 버블링은 **이벤트 객체**의 `stopPropagation` 메소드로 전파를 막을 수 있다.

 ****

## **이벤트 위임 (Event Delegation)**

- 버블링 개념을 활용하면 훨씬 효과적인 이벤트 관리를 할 수 있다.
- 부모 요소에서 한 번에 자식 요소들에 발생한 이벤트를 관리할 수도 있다.
- 자식 요소의 이벤트를 부모 요소에 위임한다고 해서 **이벤트 위임(Event Delegation)**이라고 부른다.

## **브라우저의 기본 동작**

- 브라우저에는 각 태그별 혹은 상황별로 기본적으로 약속된 동작들이 있다.
- 이러한 동작들을 막고 싶다면 **이벤트 객체**의 `preventDefault` 메소드를 통해 막을 수가 있다.

## 마우스 버튼 이벤트

```jsx
MouseEvent.button
```

| 값 | 내용 |
| --- | --- |
| 0 | 마우스 왼쪽 버튼 |
| 1 | 마우스 휠 |
| 2 | 마우스 오른쪽 버튼 |
| 3 | X1 (일반적으로 브라우저 뒤로 가기 버튼) |
| 4 | X2 (일반적으로 브라우저 앞으로 가기 버튼) |

```jsx
MouseEvent.type
```

| 이벤트 타입 | 설명 |
| --- | --- |
| mousedown | 마우스 버튼을 누르는 순간 |
| mouseup | 마우스 버튼을 눌렀다 떼는 순간 |
| click | 왼쪽 버튼을 클릭한 순간 |
| dblclick | 왼쪽 버튼을 빠르게 두 번 클릭한 순간 |
| contextmenu | 오른쪽 버튼을 클릭한 순간 |
| mousemove | 마우스를 움직이는 순간 |
| mouseover | 마우스 포인터가 요소 위로 올라온 순간 |
| mouseout | 마우스 포인터가 요소에서 벗어나는 순간 |
| mouseenter | 마우스 포인터가 요소 위로 올라온 순간 (버블링이 일어나지 않음) |
| mouseleave | 마우스 포인터가 요소에서 벗어나는 순간 (버블링이 일어나지 않음) |

## **MouseEvent.위치프로퍼티**

| 프로퍼티 | 설명 |
| --- | --- |
| clientX, clientY | 마우스 포인터의 브라우저 표시 영역에서의 위치 |
| pageX, pageY | 마우스 커서의 문서 영역에서의 위치 |
| offsetX, offsetY | 마우스 포인터의 이벤트 발생한 요소에서의 위치 |
| screenX, screenY | 마우스 포인터의 모니터 화면 영역에서의 위치 |

## **MouseEvent.relatedTarget**

- `mouseenter, mouseleave, mouseover, mouseout` 이벤트에는 `relatedTarget`이라는 프로퍼티가 존재한다.
- `relatedTarget` 프로퍼티는 이벤트가 발생하기 직전(또는 직후)에 마우스가 위치해 있던 요소를 담고 있다.

## **KeyboardEvent.type**

| 이벤트 타입 | 설명 |
| --- | --- |
| keydown | 키보드의 버튼을 누르는 순간 |
| keypress | 키보드의 버튼을 누르는 순간 ('a', '5' 등 출력이 가능한 키에서만 동작하며, Shift, Esc 등의 키에는 반응하지 않음) |
| keyup | 키보드의 버튼을 눌렀다 떼는 순간 |

++ `key`는 사용자가 누른 키가 가지고 있는 값을 나타내고 `code`는 누른 키의 물리적인 위치를 나타낸다.

## **input태그 다루기**

| 이벤트 타입 | 설명 |
| --- | --- |
| focusin | 요소에 포커스가 되는 순간 |
| focusout | 요소에 포커스가 빠져나가는 순간 |
| focus | 요소에 포커스가 되는 순간 (버블링이 일어나지 않음) |
| blur | 요소에 포커스가 빠져나가는 순간 (버블링이 일어나지 않음) |
| change | 입력된 값이 바뀌는 순간 |
| input | 값이 입력되는 순간 |
| select | 입력 양식의 하나가 선택되는 순간 |
| submit | 폼을 전송하는 순간 |

## **스크롤 이벤트**

- `scroll` 이벤트는 보통 `window` 객체에 이벤트 핸들러를 등록하고 `window` 객체의 프로퍼티와 함께 자주 활용된다.
- `scrollY` 프로퍼티를 활용하면 스크롤된 특정한 위치를 기준으로 이벤트 핸들러가 동작하게 하거나 혹은 스크롤 방향(위로 스크롤 중인지/아래로 스크롤 중인지)을 기준으로 이벤트 핸들러가 동작하게끔 활용할 수도 있다.

# 모던 자바스크립트

## 모던 자바스크립트란?

- 현 시점에서 사용하기 적합한 범위 내에서 최신 버전의 표준을 준수하는 자바 스크립트다.

### ECMAScript

- 자바 스크립트의 표준 명세서다.
- ecma라는 국제 표준화 기구에서 자바 스크립트 버전 관리를 한다.
- 자바 스크립트를 사용할 떄 준수해야 하는 규칙이나 세부 사항들을 ECMA - 262에 저장하는 데 이 문서가 ECMAScrip다.
- 1997년에 만들어져서 업데이트 될 때마다 ECMAScript1,  ECMAScript2, ECMAScript3, …처럼 이름을 붙였다.
- ES6 이후로는 1년마다 업데이트 하기로 결정했다. (ES6+/ ES6 이후의 문서들)

### **JavaScript vs ECMAScript**

- JavaScript는 프로그래밍 언어이고, ECMAScript는 프로그래밍 언어의 표준이다.
- ECMAScript는 JavaScript가 갖추어야 할 내용을 정리해둔 '설명서'이고, JavaScript는 ECMAScript를 준수해서 만들어낸 '결과물' 이다.
- ECMAScript는 JavaScript 뿐만아니라 모든 스크립트 언어(scripting languages)가 지켜야 하는 표준이다.
- JavaScript는 ECMAScript를 기반으로 하지만 ECMAScript에 정의된 내용뿐만 아니라, 다른 부가적인 기능도 있다

## 자바스크립트의 데이터 타입

- 자바스크립트는 데이터 타입이 유연한 프로그래밍 언어다.
1. number
2. string
3. boolean
4. undefined
5. null
6. object
7. symbol
8. bigint

## **Truthy 값과 Falsy 값**

- false 처럼 평가되는 값을 falsy 값, true 처럼 평가되는 값을 truthy값이라고 부른다.
- falsy값에는 false, null, undefined, 0, NaN,” “이 있다.
- truthy값은 falsy값을 제외한 모든 값이다.

## 논리 연산자

- AND와 OR연산자는 무조건 불린 값을 리턴하는게 아니라, 왼쪽 피연산자 값의 유형에 따라서 두 피연산자 중 하나를 리턴하는 방식으로 동작한다.
- AND 연산자는 왼쪽 피연산자가 falsy값일 때 왼쪽 피연산자를, 왼쪽 피연산자가 truthy값일 때 오른쪽 피연산자를 리턴한다.
- OR 연산자는 왼쪽 피연산자가 falsy 일 때 오른쪽 피연산자를, 왼쪽 피연산자가 truthy 일 때 왼쪽 피연산자를 리턴한다.

## **자바스크립트의 변수 선언 방식**

### var  특징

1. 변수 이름 중복선언 가능하다
2. 변수 선언 전에 사용 가능하다(호이스팅),
3. 함수 스코프 (함수를 기준으로 스코프를 구분한다)

### let과 const

1. 변수 이름 중복선언 불가 (SyntaxError 발생)
2. 변수 선언 전에 사용 불가 (ReferenceError 발생)
3. 블록 스코프 (중괄호로 감싸진 코드 블록에 따라 유효 범위를 구분한다)
4. const는 값을 재할당 할 수 없다.

## **함수 선언(function declaration)하기**

```jsx
// 함수 선언
function 함수이름() {
  내용;
}
```

## **함수 표현식(function expression)**

```jsx
// 함수 표현식
const 변수명 = function () {
  내용;
};
```

- 함수는 값으로 취급될 수도 있기 때문에 변수에 할당해서 함수를 선언할 수도 있다.

## **함수의 형태**

```jsx
// 변수에 할당해서 활용
const 변수명 = function () {
  내용;
};

// 객체의 메소드로 활용
const 객체명 = {
  printTitle: function () {
    내용;
  }
}

// 콜백 함수로 활용
myBtn.addEventListener('click', function () {
  console.log('button is clicked!');
});

// 고차 함수로 활용
function 합수명() {
  return function () {
    내용;
  };
};
```

## **파라미터의 기본값**

- 함수의 파라미터는 기본값을 가질 수가 있다.
- 기본값이 있는 파라미터는 함수를 호출할 때 아규먼트를 전달하지 않으면, 함수 내부의 동작은 이 파라미터의 기본값을 가지고 동작한다.

```jsx
function simple(name = 'World') {
  console.log(`Hello! ${name}`);
}

simple('sum'); // Hello! sum
simple(); // Hello! World
```

## **arguments 객체**

- `arguments` 객체는 함수를 호출할 때 전달한 아규먼트들을 배열의 형태로 모아둔 유사 배열 객체다.

```jsx
function printArguments() {
  // arguments 객체의 요소들을 하나씩 출력
  for (const arg of arguments) {
    console.log(arg); 
  }
}

printArguments('Young', 'Mark', 'Koby');
```

## **Rest Parameter**

- 파라미터 앞에 마침표 세 개를 붙여주면, 여러 개로 전달되는 아규먼트들을 배열로 다룰 수가 있게 된다.
- `arguments`객체는 유사 배열이기 때문에 배열의 메소드를 활용할 수 없는 반면, rest parameter는 배열이기 때문에 배열의 메소드를 자유롭게 사용할 수 있다.

```jsx
function printRankingList(first, second, ...others) {
  console.log('코드잇 레이스 최종 결과');
  console.log(`우승: ${first}`);
  console.log(`준우승: ${second}`);
  for (const arg of others) {
    console.log(`참가자: ${arg}`);
  }
}

printRankingList('Tommy', 'Jerry', 'Suri', 'Sunny', 'Jack');
```

- 위의 사례처럼 다른 일반 파라미터들과 함께 사용될 수도 있다.
- 앞에 정의된 파라미터에 argument를 먼저 할당하고 나머지 argument를 배열로 묶는 역할을 하기 때문에  가장 마지막에 작성해야 한다.

## **Arrow Function**

- 익명 함수를 좀 더 간결하게 표현할 수 있도록 한다.
- 함수를 정의할 때 활용될 수도 있고 콜백 함수로 전달할 때 활용할 수도 있다.
- arguments 객체가 없고, this가 가리키는 값이 일반 함수와 다르다.

```jsx
// 화살표 함수 정의
const getTwice = (number) => {
  return number * 2;
};

// 콜백 함수로 활용
myBtn.addEventListener('click', () => {
  console.log('button is clicked!');
});
```

```jsx
축약형!!
// 1. 함수의 파라미터가 하나 뿐일 때
const getTwice = (number) => {
  return number * 2;
};

// 파라미터를 감싸는 소괄호 생략 가능
const getTwice = number => {
  return number * 2;
};

// 2. 함수 동작 부분이 return문만 있을 때
const sum = (a, b) => {
  return a + b;
};

// return문과 중괄호 생략 가능
const sum = (a, b) => a + b;
```

## this

- 웹 브라우저에서 this가 사용될 때는 전역 객체, Window 객체를 가지게 된다.
- 객체의 메소드를 정의하기 위한 함수 안에선 메소드를 호출한 객체를 가리키게 된다.

## 문장과 표현식

### 문장 **(statements)**

- 문장은 어떤 동작이 일어나도록 작성된 최소한의 코드 덩어리를 말한다.
- 표현식이 아닌 문장은 문장 자체의 코드 블록(중괄호)로 그 문장의 범위가 구분된다.

### **표현식 (expressions)**

- 표현식은 길이와는 상관없이 결과적으로 하나의 값이 되는 모든 코드를 말한다.
- 표현식인 문장은 세미콜론으로 범위가 구분된다.

++ 표현식은 보통 문장의 일부로 쓰이지만, 그 자체로 문장일 수도 있다. ex) 할당식, 함수 호출

## **조건부 연산자 (Conditional operator)**

- 자바스크립트에서 세 개의 피연산자를 가지는 유일한 연산자로 조건에 따라 값을 결정할 때 활용된다.
- 삼항 연산자 (Ternary operator)라고도 불린다.
- 간결하지만 표현식이 아닌 문장은 작성할 수 없다.

```jsx
const 변수명 = (아규먼트) => 비교1 > 비교2 ? true일 때 : false일 때;

const passChecker = (score) => score > cutOff ? '합격입니다!' : '불합격입니다!';
```

## **Spread 구문**

- 여러 개의 값을 묶어놓은 배열이나 객체와 같은 값은 바로 앞에 마침표 세 개를 붙여서 펼칠 수가 있다.
- 배열은 객체로 펼칠 수 있지만 객체는 배열로 펼칠 수 없다.

```jsx
const webPublishing = ['HTML', 'CSS'];
const interactiveWeb = [...webPublishing, 'JavaScript'];

const arr1 = [1, 2, 3];
const arr2 = [4, 5, 6];
const arr3 = [...arr1, ...arr2];
```

```jsx
const members = ['태호', '종훈', '우재'];
const newObject = { ...members };  -> 가능

const topic = {
  name: '모던 자바스크립트'
}
const newArray = [...topic]; -> 불가
```

## **모던한 프로퍼티 표기법**

- ES2015 이후부터는 자바스크립트에서 변수나 함수룰 활용해서 프로퍼티를 만들 때 프로퍼티 네임과 변수나 함수 이름이 같다면 다음과 같이 축약해서 사용할 수 있다.

```jsx
function sayHi() {
  console.log('Hi!');
}

const title = 'codeit';
const birth = 2017;
const job = '프로그래밍 강사';

const user = {
  title, 
  birth, 
  job, 
  sayHi,
};

console.log(user); // {title: "codeit", birth: 2017, job: "프로그래밍 강사", sayHi: ƒ}
```

```jsx
const user = {
  firstName: 'Tess',
  lastName: 'Jang',
  getFullName() {
    return `${this.firstName} ${this.lastName}`;
  },
};

console.log(user.getFullName()); // Tess Jang
```

## **구조 분해 (Destructuring)**

- 내부에 여러 값을 담고 있는 데이터 타입을 다룰 때 Destructuring 문법을 활용하면, 배열의 요소나 객체의 프로퍼티 값들을 개별적인 변수에 따로 따로 할당해서 다룰 수가 있다.
- 기본값과 rest 문법을 활용할 수 있다.

```jsx
// Array Destructuring
const members = ['코딩하는효준', '글쓰는유나', '편집하는민환'];
const [macbook, ipad, coupon] = members;

console.log(macbook); // 코딩하는효준
console.log(ipad); // 글쓰는유나
console.log(coupon); // 편집하는민환

// Object Destructuring
const macbookPro = {
  title: '맥북 프로 16형',
  price: 3690000,
};

const { title, price } = macbookPro;

console.log(title); // 맥북 프로 16형
console.log(price); // 3690000
```

## **에러와 에러 객체**

- 에러가 발생하면 에러에 대한 정보를 `name`과 `message`라는 프로퍼티로 담고 있는 에러 객체가 만들어진다.
- 대표적인 에러 객체는 SyntaxError, ReferenceError, TypeError 다.
- `new` 키워드와 에러 객체 이름을 딴 함수를 통해 에러 객체를 만들 수 있고, `throw` 키워드로 에러를 발생시킬 수 있다.

```jsx
throw new TypeError('타입 에러가 발생했습니다.');
```

## **try...catch문**

```jsx
try {
  // 실행할 코드
} catch (error) {
  // 에러 발생 시 동작할 코드
}finally {
  // 항상 실행할 코드
}
```

- 대표적인 에러 처리 방법이다.
- `try`문에서 발생한 에러 객체가 `catch`문의 첫 번째 파라미터로 전달된다.
- `try...catch`문에서 에러의 유무와 상관없이 항상 동작해야 할 코드가 필요하다면 `finally`문을 활용할 수 있다.

## **forEach 메소드**

- 배열의 요소를 하나씩 살펴보면서 반복 작업을 하는 메소드다.
- `forEach` 메소드는 첫 번째 아규먼트로 콜백 함수를 전달받는다.
- 콜백 함수의 파라미터에는 각각 배열의 요소, index, 메소드를 호출한 배열이 전달된다. (index와 array는 생략가능)

```jsx
const numbers = [1, 2, 3];

numbers.forEach((element, index, array) => {
  console.log(element); // 순서대로 콘솔에 1, 2, 3이 한 줄씩 출력됨.
});
```

## **map 메소드**

- 배열의 요소를 하나씩 살펴보면서 반복 작업을 하는 메소드다.
- 첫 번째 아규먼트로 전달하는 콜백 함수가 매번 리턴하는 값들을 모아서 새로운 배열을 만들어 리턴하는 특징이 있다.

```jsx
const numbers = [1, 2, 3];
const twiceNumbers = numbers.map((element, index, array) => {
  return element * 2;
});

console.log(twiceNumbers); // (3) [2, 4, 6]
```

## **filter 메소드**

- 배열의 요소를 하나씩 살펴보면서 콜백함수가 리턴하는 조건과 일치하는 요소만 모아서 새로운 배열을 리턴하는 메소드다.

```jsx
const devices = [
  {name: 'GalaxyNote', brand: 'Samsung'},
  {name: 'MacbookPro', brand: 'Apple'},
  {name: 'Gram', brand: 'LG'},
  {name: 'SurfacePro', brand: 'Microsoft'},
  {name: 'ZenBook', brand: 'Asus'},
  {name: 'MacbookAir', brand: 'Apple'},
];

const apples = devices.filter((element, index, array) => {
  return element.brand === 'Apple';
});

console.log(apples); // (2) [{name: "MacbookPro", brand: "Apple"}, {name: "MacbookAir", brand: "Apple"}]
```

## **find 메소드**

- 배열의 요소들을 반복하는 중에 콜백함수가 리턴하는 조건과 일치하는 가장 첫번째 요소를 리턴하고 반복을 종료하는 메소드다.

```jsx
const devices = [
  {name: 'GalaxyNote', brand: 'Samsung'},
  {name: 'MacbookPro', brand: 'Apple'},
  {name: 'Gram', brand: 'LG'},
  {name: 'SurfacePro', brand: 'Microsoft'},
  {name: 'ZenBook', brand: 'Asus'},
  {name: 'MacbookAir', brand: 'Apple'},
];

const myLaptop = devices.find((element, index, array) => {
  console.log(index); // 콘솔에는 0, 1, 2까지만 출력됨.
  return element.name === 'Gram';
});

console.log(myLaptop); // {name: "Gram", brand: "LG"}
```

## **some 메소드**

- 배열 안에 콜백함수가 리턴하는 조건을 만족하는 요소가 1개 이상 있는지를 확인하는 메소드다.
- 배열을 반복하면서 모든 요소가 콜백함수가 리턴하는 조건을 만족하지 않는다면 `false`를 리턴하고, 배열을 반복하면서 콜백함수가 리턴하는 조건을 만족하는 요소가 등장한다면 바로 `true`를 리턴하고 반복을 종료한다.

```jsx
const numbers = [1, 3, 5, 7, 9];

// some: 조건을 만족하는 요소가 1개 이상 있는지
const someReturn = numbers.some((element, index, array) => {
  console.log(index); // 콘솔에는 0, 1, 2, 3까지만 출력됨.
  return element > 5;
});

console.log(someReturn); // true;

```

## **every 메소드**

- 배열 안에 콜백 함수가 리턴하는 조건을 만족하지 않는 요소가 1개 이상 있는지를 확인하는 메소드다.
- 배열을 반복하면서 모든 요소가 콜백함수가 리턴하는 조건을 만족한다면 `true`를 리턴하고, 배열을 반복하면서 콜백함수가 리턴하는 조건을 만족하지 않는 요소가 등장한다면 바로 `false`를 리턴하고 반복을 종료한다.

```jsx
const numbers = [1, 3, 5, 7, 9];

// every: 조건을 만족하지 않는 요소가 1개 이상 있는지
const everyReturn = numbers.every((element, index, array) => {
  console.log(index); // 콘솔에는 0까지만 출력됨.
  return element > 5;
});

console.log(everyReturn); // false;
```

## **reduce 메소드**

- 누적값을 계산할 때 활용하는 메소드다.
- `reduce` 메소드는 일반적으로 두 개의 파라미터를 활용한다.
- 첫 번째는 반복 동작할 콜백함수다. 매번 실행되는 콜백함수의 리턴값이 다음에 동작할 콜백함수의 첫번째 파라미터로 전달되는데 결과적으로 마지막 콜백함수가 리턴하는 값이 `reduce` 메소드의 최종 리턴값이 된다.
- 메소드의 두 번째 파라미터로 전달한 초기값이 첫 번째로 실행될 콜백함수의 가장 첫 번째 파라미터로 전달된다.

```jsx
const numbers = [1, 2, 3, 4];

// reduce
const sumAll = numbers.reduce((accumulator, element, index, array) => {
  return accumulator + element;
}, 0);

console.log(sumAll); // 10
```

## sort 메소드

- 배열을 정렬할 수 있다.
- 아무런 아규먼트도 전달하지 않을 때는 기본적으로 [유니코드](https://ko.wikipedia.org/wiki/%EC%9C%A0%EB%8B%88%EC%BD%94%EB%93%9C)에 정의된 문자열 순서에 따라 정렬된다.

```jsx
const letters = ['D', 'C', 'E', 'B', 'A'];
const numbers = [1, 10, 4, 21, 36000];

letters.sort();
numbers.sort();

console.log(letters); // (5) ["A", "B", "C", "D", "E"]
console.log(numbers); // (5) [1, 10, 21, 36000, 4]
```

## **reverse 메소드**

- 배열의 순서를 뒤집어 주는 메소드다.

```jsx
const letters = ['a', 'c', 'b'];
const numbers = [421, 721, 353];

letters.reverse();
numbers.reverse();

console.log(letters); // (3) ["b", "c", "a"]
console.log(numbers); // (3) [353, 721, 421]
```

## **Map**

- 이름이 있는 데이터를 저장한다는 점에서 객체와 비슷하다.
- Map은 메소드를 통해서 값을 추가하거나 접근할 수 있다.
- `new` 키워드를 통해서 Map을 만들 수 있고 아래와 같은 메소드를 통해 Map 안의 여러 값들을 다룰 수 있다.

- map.set(key, value): key를 이용해 value를 추가하는 메소드.
- map.get(key): key에 해당하는 값을 얻는 메소드. key가 존재하지 않으면 undefined를 반환.
- map.has(key): key가 존재하면 true, 존재하지 않으면 false를 반환하는 메소드.
- map.delete(key): key에 해당하는 값을 삭제하는 메소드.
- map.clear(): Map 안의 모든 요소를 제거하는 메소드.
- map.size: 요소의 개수를 반환하는 프로퍼티. (메소드가 아닌 점 주의! 배열의 length 프로퍼티와 같은 역할)

## **Set**

- 여러 개의 값을 순서대로 저장한다.
- 배열의 메소드는 활용할 수 없고 Map과 비슷하게 Set만의 메소드를 통해서 값을 다루는 특징이 있다.
- `new` 키워드로 Set을 만들 수 있고 아래와 같은 메소드를 통해 Set 안의 여러 값들을 다룰 수 있다.
- set.add(value): 값을 추가하는 메소드. (메소드를 호출한 자리에는 추가된 값을 가진 Set 자신을 반환.)
- set.has(value): Set 안에 값이 존재하면 true, 아니면 false를 반환하는 메소드.
- set.delete(value): 값을 제거하는 메소드. (메소드를 호출한 자리에는 셋 내에 값이 있어서 제거에 성공하면 true, 아니면 false를 반환.)
- set.clear(): Set 안의 모든 요소를 제거하는 메소드.
- set.size: 요소의 개수를 반환하는 프로퍼티. (메소드가 아닌 점 주의! 배열의 length 프로퍼티와 같은 역할)

## 모듈이란?

- 많은 코드가 필요한 프로그램은 하나의 파일로 관리하는 것이 아니라 각 기능 별로 여러 개의 파일로 분리하는 것이 좋다.
- 공통된 기능이나 특별한 목적에 따라 각각의 파일로 구분하는 과정을 모듈화라 그러고 각각의 파일을 모듈이라고 한다.
- 모듈화는 코드를 효율적으로 관리할 수 있고 다른 프로그램에서 재활용 할 수 있다는 장점이 있다.

### 모듈 파일의 조건

- 파일만의 독립적인 스코프를 가져야 하는데 이를 모듈 스코프라고 부른다.
- 즉, 모듈 파일 내부에서 선언한 변수나 함수는 모듈 안에서만 사용 가능하다.

```html
// 모듈 속성을 가지려면 HTML 파일에서 이렇게 type을 module로 지정해야 한다.
<script type = "module" src="printer.js"></script>
```

## 모듈 문법

- export를 통해 다른 모듈에서도 변수와 함수를 사용하게 만들 수 있다.
- export를 선언 앞에 붙이기
- 변수나 함수를 사용하고자 하는 파일에서 import를 이용해 불러와야 쓸 수 있다.

```jsx
export const 변수명/함수명 = 값;

// 그 변수를 쓸 다른 파일
import { title, print } from './export가 쓰여진 파일 이름'
```

## 이름 바꾸기

- import 한 변수의 이름이 모듈에서 쓰고자 한 이름과 같을 때 import 한 변수의 이름을 바꿔줘야 한다.

```jsx
import { title, print } from './export가 쓰여진 파일 이름'

const title = '바꿀 이름';

//또는 import { title as 바꿀 이름, print } from './export가 쓰여진 파일 이름'
```

## 한꺼번에 다루기

```jsx
import * as 새로운 이름 from './export가 쓰여진 파일 이름'

//사용할 때는 객체 형식으로
새로운 이름.print(이름)

//한꺼번에 export 가능
코드 맨 밑에 export {할 것들}
```

- `*` 를 와일드 카드 문자라고 한다.

## default export

- `export default` 는 반드시 하나의 대상만 내보낼 수 있다.
- 모듈 파일 내에서 딱 하나만 사용할 수 있다.

```jsx
export default '값';

//사용할 때 이름을 붙여줘야 한다.

default as 이름;

// 또는 디폴트 에스를 생략하고 중괄호 밖으로 빼낼 수 있다.
import 이름, {
...
}

// 여러 개 export
export default {title, print };
// == export default {title: title, print: print };
```

# 자바스크립트 객체 지향 기본기

## 객체와 class

### 객체 지향 프로그래밍이란?

- ‘객체’ 간의 상호작용을 중심으로 하는 프로그래밍이다.
- 프로퍼티와 메소드로 이루어진 각 객체들의 상호 작용을 중심으로 코드를 작성하는 것이다.

### 객체란?

- 객체의 상태를 나타내는 변수 → 프로퍼티
- 객체의 행동을 나타내는 함수로 이루어져 있다. →메소드

++ Object Literal →객체를 나타내는 문자열

### Object Literal

- 객체를 나타내는 문자열

```jsx
const user = {
    email,
    birthdate,
    buy(item) {
      console.log(`${this.email} buys ${item.name}`);
    },
  };
```

### **Factory function**

```jsx
function createUser(email, birthdate) {
  const user = {
    email,
    birthdate,
    buy(item) {
      console.log(`${this.email} buys ${item.name}`);
    },
  };
  return user;
}

const user1 = createUser('chris123@google.com', '19920321');
const user2 = createUser('jerry99@google.com', '19950719');
```

- 함수 안에  Object Literal을 포함해 만들어 객체를 만들어낼 수 있다.
- 객체를 생성해서 return 한다.

### **Constructor function**

```jsx
function User(email, birthdate) {
  this.email = email;
  this.birthdate = birthdate;
  this.buy = function (item) {
    console.log(`${this.email} buys ${item.name}`);
  };
}

const user1 = new User('chris123@google.com', '1992-03-21');
const user2 = new User('jerry99@google.com', '1995-07-19');
```

- 객체를 생성하는 용도로 사용하는 Constructor function을 정의하고, 그 안에서 this 키워드를 사용하여 생성될 객체의 프로퍼티와 메소드를 설정하는 방법이다.
- `this` 는 현재 객체인 user 객체 자체를 의미한다.
- Constructor function으로 객체를 생성하려면 그 앞에 new를 붙여서 실행해야 한다.

## class

```jsx
class User {
  constructor(email, birthdate) {
    this.email = email;
    this.birthdate = birthdate;
  }

  buy(item) {
    console.log(`${this.email} buys ${item.name}`);
  }
}

const user1 = new User('chris123@google.com', '1992-03-21');
const user2 = new User('jerry99@google.com', '1995-07-19');
```

- class 키워드를 사용해서 객체의 틀을 정의한다.
- class를 사용할 때는 보통 프로퍼티의 경우 constructor 안에 정의하고, 메소드의 경우 constructor 밖에 정의한다.
- new를 붙여서 객체를 생성한다.

## 객체 지향 프로그래밍 핵심 개념 4가지

1. 추상화
2. 캡슐화
3. 상속
4. 다형성

## 추상화**(Abstraction)**란?

- 어떤 구체적인 존재를 원하는 방향으로 간략화해서 나타내는 것이다.

## **캡슐화(Encapsulation)**란?

- 객체 외부에서 함부로 접근하면 안되는 프로퍼티나 메소드에 직접 접근할 수 없도록 하고, 필요한 경우 공개된 다른 메소드를 통해서만 접근할 수 있도록 하는 것을 의미한다.
- 즉, 객체의 특정 프로퍼티에 직접 접근하지 못하도록 막는 것이다.
- `_email`에 접근할 수 있기에 완벽한 추상화는 아니다. (클로저 이용시 완벽한 추상화 가능)
- 객체도 캡슐화할 수 있다.

```jsx
class User {
  constructor(email, birthdate) {
    this.email = email;
    this.birthdate = birthdate;
  }

  buy(item) {
    console.log(`${this.email} buys ${item.name}`);
  }
  
  // getter 함수 , ._email 대신 email만 써도 된다.
  get email() {
    return this._email;
  }
  
  // setter 함수, email 프로퍼티에 값을 설정하려고 할때마다 실행된다. (함수가 실행되는 것)
  set email(address) {
    if (address.includes('@')) {
      this._email = address;
    } else {
      throw new Error('invalid email address');
    }
  }
}
// ._email에 접근 가능
console.log(user1._email);
user1._email = 'chris robert';
```

## 상속**(Inheritance)이란?**

- 하나의 객체가 다른 객체의 프로퍼티와 메소드를 받을 `때` 상속이라고 한다.
- 즉, 부모 클래스의 프로퍼티와 메소드를 자식 클래스가 그대로 물려받는 것이다.
- 상속을 이용하면 코드의 재사용성이 좋아진다.

```jsx
class User {
  constructor(email, birthdate) {
    this.email = email;
    this.birthdate = birthdate;
  }

  buy(item) {
    console.log(`${this.email} buys ${item.name}`);
  }
} 

class PremiumUser extends User {
  constructor(email, birthdate, level) {
    super(email, birthdate);             // 필수!!
    this.level = level;
  }

  streamMusicForFree() {
    console.log(`Free music streaming for ${this.email}`);
  }
}

++ //만약 자식 매소드에서 부모 매소드와 동일한 부분이 있으면
super.buy(item);
// 이런 식으로 쓰면 된다. 
```

## **다형성(Polymorphism)이란?**

- 많은 형태를 가지고 있는 성질을 의미한다.
- 하나의 변수가 다양한 종류의 클래스로 만든 여러 객체를 가리킬 수 있음을 의미한다.
- 자식 클래스에서 부모 클래스의 메소드와 동일한 이름의 다른 매소드를 정의하고 내용을 다르게 만드는 것을 오버라이딩(overriding)이라고 한다.

```jsx
class User {
  constructor(email, birthdate) {
    this.email = email;
    this.birthdate = birthdate;
  }

  buy(item) {
    console.log(`${this.email} buys ${item.name}`);
  }
} 

class PremiumUser extends User {
  constructor(email, birthdate, level) {
    super(email, birthdate);
    this.level = level;
  }

  buy(item) {
    console.log(`${this.email} buys ${item.name} with a 5% discount`);
  }

  streamMusicForFree() {
    console.log(`Free music streaming for ${this.email}`);
  }
}

const item = { 
  name: '스웨터', 
  price: 30000, 
};

const user1 = new User('chris123@google.com', '19920321');
const user2 = new User('rachel@google.com', '19880516');
const user3 = new User('brian@google.com', '20051125');
const pUser1 = new PremiumUser('niceguy@google.com', '19891207', 3);
const pUser2 = new PremiumUser('helloMike@google.com', '19900915', 2);
const pUser3 = new PremiumUser('aliceKim@google.com', '20010722', 5);

const users = [user1, pUser1, user2, pUser2, user3, pUser3];

users.forEach((user) => {
  user.buy(item);
});
```

## instanceof 연산자

- 현재 변수가 가리키는 객체가 정확히 어느 클래스로 만든 객체인지 확인할 수 있다.

```jsx
users.forEach((user) => {
	// PremiumUser로 만든 객체면 true, 아니면 false 출력
	console.log(user instanceof PremiumUser);
});
```

```jsx
users.forEach((user) => {
	// 자식 클래스로 만든 객체는 부모 클래스로도 인정되기에 전부 true가 출력
	console.log(user instanceof User);
});
```

## static 프로퍼티와 static 메소드

- 클래스에 직접적으로 딸려 있는 프로퍼티와 메소드다.
- 객체가 아닌 클래스 자체로 접근하고 싶을 때 사용 한다.
- static을 붙이면 이 클래스로 객체를 생성하지 않아도 프로퍼티와 메소드를 사용할 수 있다.
- 기존 값 수정이나 새로운 값 생성 가능하다.

# 자바스크립트 웹 개발 기본기

## fetch 함수

```jsx
fetch('URL')
	.then((response) => response.text()) //return 이 생략되어 있다.
	.then((result) => {console.log(result); }); //response.text()가 result로 넘어간다.
```

- 패치는 서버로 원하는 내용을 요구하는 request를 보내고 response를 받는 함수다.
- 파라미터로 넘어온 URL로 request를 보낸다.
- 서버가 보낸 response는 하나의 객체가 되어 파라미터로 넘어온다.
- 두번째 줄은 서버로 리스폰스가 온 후에야 실행된다.
- 나중에 어떤 조건이 만족되었을 때 실행되는 함수를 콜백 함수라고 한다.
- then은 콜백을 등록해주는 매소드다. then은 패치 함수가 리턴하는 어떤 객체의 매소드다.

정리하면,

1. fetch 함수는 어떤 객체를 리턴하는데(Promise 객체)
2. 이 객체의 then 메소드로, '리스폰스가 왔을 때 실행할 콜백'을 등록할 수 있습니다.
3. 이렇게 등록된 콜백들은 then 메소드로 등록한 순서대로 실행되고, 이때 이전 콜백의 리턴값을 이후 콜백이 넘겨받아서 사용할 수 있다.

## **개발자 도구란?**

- 웹 브라우저가 내부적으로 어떤 동작을 하고 있는지 살펴보게 해주는 도구다.
- 개발자 도구를 사용해서 자신이 작성한 코드를 브라우저가 어떻게 해석하고 실행하는지 자세하게 살펴볼 수 있다.
- Ctrl 키 + Shift 키 + 알파벳 i 키 가 단축키다.

## URL(Uniform Resource Locator)이란?

- 웹에 존재하는 특정 데이터를 나타내기 위한 문자열이다.
- 화면에서 클릭하는 버튼 등에 어느 URL로 새로운 리퀘스트를 보낼지, HTML 코드 또는 Javascript 코드로 다 작성이 되어있기 때문에 호스트 부분만 입력해도 페이지로 진입한다.

### URL 구성

- 스킴(Scheme)
    - 프로토콜의 이름
    - http = HyperText Transfer Protocol
- 호스트 (Host)
    - 전 세계 서버 중 하나의 서버를 특정한다.
- 경로 (Path)
    - 서버에 있는 데이터 중 원하는 데이터를 특정한다.
    - 설계하는 개발자에 따라 다르다.
- 쿼리 (Query)
    - 존재할 때도, 존재하지 않을 때도 있다.
    - 데이터에 관한 세부적인 요구 사항이 있을 때 사용한다.
    - 설계하는 개발자에 따라 다르다.

## JSON이란?

- Java Script Object Notation
- JSON에서는 각 프로퍼티의 이름을 반드시 큰따옴표(")로 감싸줘야 한다.
- JSON에서는 값이 문자열인 경우 큰따옴표(")를 사용해야 한다.
- JSON에서는 표현할 수 없는 값들이 있습니다. (undefined, NaN, Infinity)
- JSON에는 주석을 추가할 수 없다.

```jsx
fetch('URL')
	.then((response) => response.text()) 
	.then((result) => { const users = JSON.parse(result) }); 
```

## 메소드의 의미

| 메소드 | 데이터 처리 |
| --- | --- |
| GET | READ (데이터 조회) |
| POST | CREATE (데이터 추가) |
| PUT | UPDATE (데이터 수정) |
| DELETE | DELETE (데이터 삭제) |

## Request

- Head는 Request에 대한 부가 정보 (메소드)
- Body는 실제 데이터를 담는 부분이다.

```jsx
...
:method: GET
:path: /men/shirts
...
헤더 1: 값
헤더 2: 값
헤더 3: 값
...
```

## POST request

- Request Payload라고 쓰인 부분이 바로 리퀘스트의 바디 부분이다.

```jsx
fetch('URL'), {
	method: 'POST',
	body: JSON.stringify(newMember),
})  
	.then((response) => response.text()) 
	.then((result) => { console.log(result) }); 
```

## PUT request

```jsx
fetch('URL'), {
	method: 'PUT',
	body: JSON.stringify(newMember),
})  
	.then((response) => response.text()) 
	.then((result) => { console.log(result) }); 
```

## DELETE request

```jsx
fetch('URL'), {
	method: 'DELETE',
})  
	.then((response) => response.text()) 
	.then((result) => { console.log(result) }); 
```

## API?

- Application Programming Interface의 약자다.
- ‘개발할 때 사용할 수 있도록 특정 라이브러리나 플랫폼 등이 제공하는 데이터나 함수 등'을 의미한다.
- 웹 개발에서는 어느 URL로 어떤 리퀘스트를 보냈을 때, 무슨 처리가 수행되고 어떤 리스폰스가 오는지에 관해 미리 정해진 규격을 **Web API**라고도 한다.
- Web API를 설계한다는 것은 서비스에서 사용될 모든 URL들을 나열하고, 각각의 URL에 관한 예상 리퀘스트와 리스폰스의 내용을 정리한다는 뜻이다.

## **REST API?**

- Web API 설계를 할 때, 준수하기 위해 노력하는 일종의 가이드라인이다.
- Representational State Transfer(표현적인 상태 이전)의 줄임말이다.
- REST architecture가 되기 위한 조건
- Client-Server
    
    Client-Server 구조를 통해 양측의 관심사를 분리해야 한다.
    
- Stateless
    
    Client가 보낸 각 리퀘스트에 관해서 Server는 그 어떤 맥락(context)도 저장하지 않는다.
    
- Cache
    
    Cache를 활용해서 네트워크 비용을 절감해야 한다.
    
- Uniform Interface
    
    Client가 Server와 통신하는 인터페이스는 다음과 같은 하위 조건 4가지를 준수해야 한다.
    
- Layered System
- Code on Demand

## status code

- 모든 상태 코드(Status Code)는 각각 그에 대응되는 상태 메시지(Status Message)를 갖고 있다.

### **100번대**

서버가 클라이언트에게 **정보성 응답**(Informational response)을 줄 때 사용되는 상태 코드들이다.

- **100 Continue** : 클라이언트가 서버에게 계속 리퀘스트를 보내도 괜찮은지 물어봤을 때, 계속 리퀘스트를 보내도 괜찮다고 알려주는 상태 코드다.
- **101 Switching Protocols** : 클라이언트가 프로토콜을 바꾸자는 리퀘스트를 보냈을 때, 서버가 '그래요, 그 프로토콜로 전환하겠습니다'라는 뜻을 나타낼 때 쓰이는 상태 코드다.

### **200번대**

클라이언트의 리퀘스트가 성공 처리되었음을 의미하는 상태 코드들이다.

- **200 OK** : 리퀘스트가 성공적으로 처리되었음을 포괄적으로 의미하는 상태 코드다. GET 리퀘스트의 경우 리소스가 잘 조회되었다는 뜻이고, POST 리퀘스트의 경우 새 리소스가 잘 생성되었다, PUT 리퀘스트의 경우 기존 리소스가 잘 수정되었다, DELETE 리퀘스트의 경우 기존 리소스가 잘 삭제되었다는 뜻이다.
- **201 Created** : 리퀘스트의 내용대로 리소스가 잘 생성되었다는 뜻이다. POST 리퀘스트가 성공한 경우에 200번 대신 201번이 올 수도 있다.
- **202 Accepted** : 리퀘스트의 내용이 일단은 잘 접수되었다는 뜻이다. 즉, 당장 리퀘스트의 내용이 처리된 것은 아니지만 언젠가 처리할 것이라는 뜻이다.

### **300번대**

클라이언트의 리퀘스트가 아직 처리되지 않았고, 리퀘스트 처리를 원하면 클라이언트 측의 추가적인 작업이 필요함을 의미하는 상태 코드들이다.

- **301 Moved Permanently** : 리소스의 위치가 바뀌었음을 나타낸다.
- **302 Found** : 리소스의 위치가 일시적으로 바뀌었음을 나타낸다. 이 말은 지금 당장은 아니지만 나중에는 현재 요청한 URL이 정상적으로 인식될 것이라는 뜻이다.
- **304 Not Modified** : 브라우저들은 보통 한번 리스폰스로 받았던 이미지 같은 리소스들을 그대로 내부에 저장하고 있다. 그리고 서버는 해당 리소스가 바뀌지 않았다면, 리스폰스에 그 리소스를 보내지 않고 304번 상태 코드만 헤드에 담아서 보냄으로써 '네트워크 비용'을 절약하고 브라우저가 저장된 리소스를 재활용하도록 한다.

### **400번대**

리퀘스트를 보내는 클라이언트 쪽에 문제가 있음을 의미하는 상태 코드들이다.

- **400 Bad Request** : 말그대로 리퀘스트에 문제가 있음을 나타낸다. 리퀘스트 내부 내용의 문법에 오류가 존재하는 등의 이유로 인해 발생한다.
- **401 Unauthorized** : 아직 신원이 확인되지 않은(unauthenticated) 사용자로부터 온 리퀘스트를 처리할 수 없다는 뜻이다.
- **403 Forbidden** : 사용자의 신원은 확인되었지만 해당 리소스에 대한 접근 권한이 없는 사용자라서 리퀘스트를 처리할 수 없다는 뜻이다.
- **404 Not Found** : 해당 URL이 나타내는 리소스를 찾을 수 없다는 뜻이다.
- **405 Method Not Allowed** : 해당 리소스에 대해서 요구한 처리는 허용되지 않는다는 뜻이다.
- **413 Payload Too Large** : 현재 리퀘스트의 바디에 들어있는 데이터의 용량이 지나치게 커서 서버가 거부한다는 뜻이다.
- **429 Too Many Requests** : 일정 시간 동안 클라이언트가 지나치게 많은 리퀘스트를 보냈다는 뜻이다.

### **500번대**

서버 쪽의 문제로 인해 리퀘스트를 정상적으로 처리할 수 없음을 의미하는 상태 코드들이다.

- **500 Internal Server Error** : 현재 알 수 없는 서버 내의 에러로 인해 리퀘스트를 처리할 수 없다는 뜻이다.
- **503 Service Unavailable** : 현재 서버 점검 중이거나, 트래픽 폭주 등으로 인해 서비스를 제공할 수 없다는 뜻이다.

## **Content-Type 헤더**

- 현재 리퀘스트 또는 리스폰스의 바디에 들어 있는 데이터가 어떤 타입인지를 나타낸다.
- Content-Type 헤더의 값은 '주 타입(main type)/서브 타입(sub type)'의 형식으로 나타난다.