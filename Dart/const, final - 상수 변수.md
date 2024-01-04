# const, final - 상수 변수
상수 변수는 초깃값을 대입한 후 값을 바꿀 수 없다.

<br>

## const - 컴파일 타임 상수 변수
- 컴파일 타임 상수 변수는 `const` 예약어로 선언한다.
- 클래스에 선언할 때는 `static` 변수로만 선언할 수 있다.
- 컴파일 단계에서 상수가 된다.
- 따라서 변수를 선언할 때 초깃값을 대입해야 한다.

```dart
const String data1 = 'First Data';

class DartClass {
    static const String data2 = 'Second Data';

    void DartFunction() {
        const String data3 = 'Third Data';
    }
}
```

### const String의 대입
- `const` 예약어로 선언한 `String` 타입 상수 변수에 문자열 템플릿으로 값을 대입할 경우, 템플릿 내부에도 컴파일 타입 상수를 사용해야 한다.
```dart
main() {
    String s1 = 'hello';
    const String s2 = s1;   // 오류 발생
}
```

<br>

## final - 런 타임 상수 변수
- 런 타임 상수 변수는 `final` 예약어로 선언한다.
- 앱이 실행될 때 값이 결정된다.
- 따라서 변수를 선언할 때 초깃값을 대입하지 않아도 된다.

```dart
final int data1;            // 이후에 값을 대입하므로

class DartClass {
    final int data2;        // 초깃값을 대입하지 않아도

    void DartFunction() {
        final int data;     // 오류가 발생하지 않는다.
    }
}
// 그러나 앱 실횅 시 값이 대입되지 않으면 오류가 발생한다.
```