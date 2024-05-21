# js

# 💫 프로그래밍 시작하기 in javascript

1. 세미콜론 / 없어도 무관 but 쓰는 것이 좋음
2. 주석 // or /* */
3. 자료형
4. 추상화 : 구체적인 정보에서 꼭 필요한 핵만을 가져온 것, 복잡->단순,
5. 변수
let variable= 3000;
console.log(variable);
6. 함수
function 함수이름() {
명령;
}
7. 파라미터(매개변수)

# 💫 프로그래밍 핵심 개념 in javascript

## 1. 자료형

1. 숫자형
거듭제곱 ** > *
2. 문자열
3. 문자열 활용 
| : "를 쓰고싶을때 →  `` : 백틱
4. bool
=== : 엄격한 비교 /
js에서는 '2' == 2 //true
'2' === 2 //false
!==
&& ||
!! (360도)
5. boolen형
6. typeof 연산자
type of 1 //'number'
type of 1.0 //'number'
type of '1' // 'string'
type of "1" // 'string'
type of `1` // 'string'
console.log(typeof 8 -3) //NAN
typeof가 연산자보다 우선순위가 높음
typeof 8 = number
number - 3 = NAN
7. typeof는 string 리턴
8. 형변환
String(), Number(), Boolean()
Boolean()의 경우 0, '' NAN -> falsy값 그 외 True
9. 형변환
console.log(4 + '2') //42
console.log(4 - true) // 2
console.log(4 / '2') //2
10. 수식연산자>비교연산자
11. 템플릿 문자열
console.log(`안녕하세요 ${name*2} 입니다.`)
12. null 과 undefined
의도적으로 값이 없다는 말/값이 없다는걸 확인할 때
선언 x -> undefined
let v = null
null == undefined //true
null === undefined //false

## 2. 추상화

1. 할당 연산자
2. 복합 할당 연산자
3. 함수의 실행 순서
4. return 문 이해하기
절대 실행 안되는 코드 : dead code
ex) return 뒤에 있는 코드
5. return vs console.log
6. 실습
console.log('문자열' * '문자열') //nan
7. 옵셔널 파라미터 = default
옵셔널 파라미터는 맨 뒤에 위치
8. 변수의 scope 범위
지역변수, 전역변수
9. 상수
const NUM = 0; //변경불가, 선언 필수, 대문자_대문자

## 3. 제어문

1. if
2. else if
3. switch (?){
case ? :
break;
defalut:
// switch는 자료형 따져서 === 써야됨
4. for
5. 실습
문자열 * 3 불가
6. while
7. break vs continue

js < < 가능?

# 💫 프로그래밍 데이터 in Javascript

## 1. 객체

1. 객체와 프로퍼티
    - 객체(object) 구성
    프로퍼티 네임 : 프로퍼티 value
    - 선언 let 객체이름 = {}
    -property name 주의 사항
    프로퍼터 네임의 자료형은 문자열이지만 반드시 따옴표로 감싸줘야 할 필요는 없다.
    - 다만 첫 번째 글자는 반드시 문자, 밑줄(_), $ 중 하나로 시작/띄어쓰기 금지/ - 금지
    의 경우는 따옴표로 감싸줘야 함
- key : value
bestCourse : { title : '제목', language : 'java' }
1. 객체 접근
2. 점표기법 객체이름.프로퍼티이름.프로퍼티이름['프로퍼티이름']
3. 대괄호 표기법 객체이름['프로퍼티이름']
없는 프로프터에 접근할 경우 undefined 나옴
4. 객체 프로퍼티에 할당, 교체 가능.
delete 객체.프로퍼티 하면 삭제가능
    
    console.log(객체.프로퍼티 !== undefined) // true : 존재 false 비존재
    console.log('name' in 객체); //객체 안에 프로퍼티가 있는지 확인 후 boolean 리턴
    두 가지가 다름 undefined일 경우.. in 연산자 사용하는 것이 좋음
    06. 실습
    07. 객체와 메소드
    메소드는 객체에 맞는 동작을 할 때(객체의 고유한 동작)
    let 객체이름 = {
    함수이름 : function() {
    실행할 함수;
    },
    함수이름 : function() {
    실행할 함수;
    }
    };
    
    객체이름.함수이름()
    객체이름['함수이름'](notion://www.notion.so/'%ED%8C%8C%EB%9D%BC%EB%AF%B8%ED%84%B0');
    
5. 실습
매개변수로 함수이름을 받을 경우 [] 로 사용
그냥 대괄호 사용이 젤 맘 편할지도
6. for in 반복문
for (let key in 객체){
함수
} // 객체에 있는 모든 프로퍼티를 돌아라
7. for in 주의사항
객체는 정수형 프로퍼티 네임을 오름차순으로 먼저 정렬하고, 나머지 프로퍼티들은 추가한 순서대로 정렬하는 특징이 있습니다.
'2' : 'value2'
'1' : 'value1'
해도 '1'이 먼저 나옴
8. 실습
9. date 객체
내장객체임.
let 객체 = new Date(1000);
1970년 1월 1일 00:00:00 utc + 1000ms(1초)
let 객체 = new Date('문자열');
'YYYY-MM-DDThh:mm:ss' // hms 없으면 자정이 디폴트
new Date(YYYY, MM, DD, hh, mm, ss, ms) //YYYY, MM은 필수, 디폴트는 1일 자정
//month는 0부터 시작하므로 5월 = 4로 써야됨
myDate.getTime() // myDate란 객체가 1970년 1월 1일 00:00:00 UTC 부터 얼마나 지났는지-> 타임스탬프
10. date 객체 tip
month // 0부터 시작
date // 일자
day // 요일(일요일 0, 토요일 6)
    
    set으로 시작하는 다양한 메서드를 활용하면, 생성된 Date객체의 정보를 수정할 수도 있습니다.
    
    (대괄호로 감싸진 요소들은 선택적인 요소입니다.)
    
    setFullYear(year, [month], [date])
    setMonth(month, [date])
    setDate(date)
    setHours(hour, [min], [sec], [ms])
    setMinutes(min, [sec], [ms])
    setSeconds(sec, [ms])
    setMilliseconds(ms)
    setTime(milliseconds)(1970년 1월 1일 00:00:00 UTC부터 밀리초 이후를 나타내는 날짜를 설정)
    
    let myDate = new Date();
    
    console.log(myDate.toLocaleDateString()); // myDate가 가진 날짜에 대한 정보 (년. 월. 일)
    console.log(myDate.toLocaleTimeString()); // myDate가 가진 시간에 대한 정보 (시:분:초)
    console.log(myDate.toLocaleString()); // myDate가 가진 날짜와 시간에 대한 정보 (년. 월. 일 시:분:초)
    toLocaleDateString(), toLocaleTimeString(), toLocaleString() 메소드는 사용자의 브라우저에 설정된 국가의 표기에 맞춰 날짜와 시간을 보여줍니다.
    
    Date 객체엔 자동으로 날짜를 수정해주는 유용한 기능이 있습니다. 범위를 벗어나는 값을 설정하려고 하면 자동으로 날짜를 수정해줍니다.
    let myDate = new Date(1988, 0, 32); // 1988년 1월 32일은 없습니다
    // 2월 1일로 자동고침 되는걸 확인할 수 있습니다.
    console.log(myDate) // Mon Feb 01 1988 00:00:00
    
    let myDate = new Date();
    console.log(Date.now() === myDate.getTime()); // true
    위 코드를 보시면 알 수 있듯이 새로운 객체를 만들어서 getTime 메소드를 호출한 값과 일치한다는 사실을 확인할 수 있는데요.
    
    let myDate = new Date(2017, 4, 18);
    
    console.log(typeof myDate); // object
    console.log(String(myDate)); // Thu May 18 2017 00:00:00 GMT+0900 (Korean Standard Time)
    console.log(Number(myDate)); // 1495033200000
    console.log(Boolean(myDate)); // true
    우리가 눈여겨 볼 부분은 number 타입으로 변환할 경우입니다.
    이 값은 아무 의미없는 단순한 숫자값이 아니라 getTime() 메소드를 활용한 것과 똑같은 수치의 타임스탬프 값 입니다.
    
    let myDate1 = new Date(2017, 4, 18);
    let myDate2 = new Date(2017, 4, 19);
    
    let timeDiff = myDate2 - myDate1;
    console.log(timeDiff); // 86400000 (ms)
    console.log(timeDiff / 1000); // 86400 (sec)
    console.log(timeDiff / 1000 / 60) // 1440 (min)
    console.log(timeDiff / 1000 / 60 / 60) // 24 (hour)
    console.log(timeDiff / 1000 / 60 / 60 / 24) // 1 (date)
    

## 2. 배열

1. 배열 let 배열이름 = [ , , , ,]
2. 배열 응용
배열도 객체다!
배열이름.length or 배열이름['length] // 배열의 요소 개수
존재하지 않는 값에 접근 -> undefined(empty)
delete 배열이름[인덱스] 하면 값은 사라지는데 메모리는 남음(empty)
3. 배열 메소드 splice
배열.splice(인덱스) // 인덱스 후부터 모두 삭제(메모리까지)
배열.splice(인덱스, 개수) // 인덱스 부터 개수만큼 삭제
배열.splice(인덱스, 개수, item1, item2 ...) // 인덱스 부터 개수만큼 삭제 후 item 삽입
개수가 0이면 추가도 가능
4. 실습
반복문으로 삭제할 때,
for ( i in 배열) 로 하면 할때마다 배열이 업데이트를 하기 때문에 제대로 work 하지 않음
for (let i = 0; i < numbers.length; i++) {
if (numbers[i] % 2 !== 0) {
numbers.splice(i, 1);
i--;
}
}
for (let i = numbers.length - 1; i >= 0; i--){
if (numbers[i]%2 == 1){
numbers.splice(i, 1)
}
}
두가지 방법
5. 배열 메소드
배열.shift() // 맨 첫 요소 삭제
배열.pop() // 맨 마지막 요소 삭제
배열.unshift('요소') // 맨 앞에 요소 삽입
배열.push('요소') // 맨 뒤에 요소 삽입
6. 배열 메소드 tip
- 배열에서 특정 값 찾기 (indexOf / lastIndexOf)
배열에서 특정 값을 찾으려면 indexOf 메소드를 사용하면 됩니다. array.indexOf(item)을 하면 array 배열에 item이 포함되어 있는지 확인할 수 있습니다.
- 만약 포함되어 있다면, item이 있는 인덱스가 리턴됩니다.
포함되어 있지 않다면, -1이 리턴됩니다.
여러 번 포함되어 있으면, 처음 발견된 인덱스가 리턴됩니다.
- lastIndexOf라는 메소드가 있는데요. indexOf와는 반대로 탐색을 뒤에서 부터 하게 됩니다.
- array.includes(item)을 하게되면 array배열에 item이 있을 경우 true를, 없을 경우 false를 리턴합니다.
- reverse라는 메소드를 활용하면, 배열의 순서를 뒤집을 수도 있습니다.
1. for .. of 반복문
for (let 요소 of 배열){
//권장
}
for (let index in 배열){
//for in은 배열에 적합하지 않음
}
2. 실습
// votes 배열을 이용해서 voteCounter 객체를 정리하기
for (let name of votes) {
// 여기에 코드를 작성하세요
if (name in voteCounter) {
voteCounter[name]+= 1;
} else {
voteCounter[name] = 1;
}
}
3. error
    
    다음 중 연산 결과가 false 인 보기를 모두 선택해 주세요.
    
    Boolean(0)//
    null !== undefined
    3 !== 1 * '3'//
    Number('5' + 3) < 10//
    String(123) * 3 <= Number('369') * true//