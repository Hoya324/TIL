# JSON이란?

JavsScript Object Notation의 약자로, 속성-값 쌍(attribute–value pairs), 배열 자료형(array data types)
또는 기타 모든 시리얼화 가능한 값(serializable value) 또는 "키-값 쌍"으로 이루어진 데이터 오브젝트를 전달하기 위해 인간이 읽으 수 있는 텍스트를 사용하는 개방형 표전 포맥이다.

즉,프로그래밍 언어나 플랫폼에서 독립적인 데이터 포맷이다.

# XML이란?

EXtensible Markup Language의 약자로, HTML과 비슷한 문자 기반 마크업 언어로 되어있지만 HTML과 달리 데이터를 보여주는 목적이 아니라 데이터르 저장하고 전달하는 목적을 가진다.

# JSON과 XML의 공통점

1. 데이터르 저장하고 전달한다.
2. 기계, 사람이 쉽게 읽을 수 있다.
3. 계층적인 데이터 구조르 가진다.
4. 다양한 프로그래밍 언어에 의해 파싱(구문 분석)될 수 있다.
5. XMLHttpRequest 객체를 이용하여 서버로부터 데이터르 전송받을 수 있다.

# JSON과 XML의 차이점

1. JSON은 종료 태그를 사용하지 않는다.
2. JSON의 구문이 XML의 구문보다 더 짧다.
3. JSON 데이터가 XML 데이터보다 더 빨리 읽고, 쓸 수 있다.
4. XML은 배열으 사용할 수 없지만, JSON은 배열을 사용할 수 있다.
5. XML은 파서로 파싱되며, JSON은 자바스크립트 표주 함수이 eval()함수로 파싱된다.

XML 예제
```xml
<dog>
    <name>식빵</name>
    <family>웰시코기<family>
    <age>1</age>
    <weight>2.14</weight>
</dog>
```

JSON 예제
```json
{
    "name": "식빵",
    "family": "웰시코기",
    "age": 1,
    "weight": 2.14
}
```

