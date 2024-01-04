# _(underscore) - Private 변수 만들기
<br>

- 다트에서는 `pubic`, `private`와 같은 접근 제한자(access modifier)를 제공하지 않는다.
- 다트에서 프로그램의 구성 요소를 선언하면 기본으로 `public` 상태가 된다.
- 다트에서 접근 범위를 한정하려면 **밑줄**(underscore)을 사용한다

<br>


``` dart
int _privateVariable = 10;

void _privateFunction() {}

class _privateClass {}
```