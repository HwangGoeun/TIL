# part, part of, library - 라이브러리를 하나로 모으기
<br>

- 여러 패키지를 한 파일 안에 집어넣고 사용하고 싶을 때 `part`, `part of`, `library` 예약어를 이용한다.

<br>

만약 a.dart, b.dart 파일을 만들고 my_lib라는 라이브러리 하나로 모두 불러오고 싶다면 다음과 같이 사용할 수 있다 :

<br>

a.dart
```dart
part of my_lib;

int aData = 10;
```
b.dart
```dart
part of my_lib;

int bData = 20;
```
myLib.dart
```dart
library my_lib;

part 'a.dart';
part 'b.dart';
```
main.dart
```dart
import 'myLib.dart';

main() {
    print('$aData, $bData');
}
```