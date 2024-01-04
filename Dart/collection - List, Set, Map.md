# collection - List, Set, Map
- `collection` 타입이란 한 변수에 여러 데이터를 저장하는 방법을 말한다.

<br>

## List
- 데이터를 여러 개 저장하고 인덱스 값으로 데이터를 이용하는 클래스
- 리스트를 선언하면서 초기화 할 때는 대괄호[] 사용
```dart
main() {
    // 리스트 생성 시 데이터 타입을 지정해주지 않으면 dynamic 타입의 리스트가 된다.
    List list1 = [1, 'Hello', true];

    // 특정 타입의 데이터를 저장하는 리스트를 선언할 때는 generic으로 명시해주면 된다.
    List<int> list2 = [10, 20, 30];
}
```

<br>

## Set
- 데이터를 여러 개 저장하고 인덱스 값으로 데이터를 이용하는 클래스
- 중복 데이터를 허용하지 않는다
- 세트를 선언하면서 초기화 할 때는 중괄호{} 사용
```dart
main() {
    Set<int> set1 = Set();
    Set<int> set2 = {10, 20, 30};
}
```

<br>

## Map
- 여러 개의 데이터를 키와 값 형태로 저장하는 클래스
- 맵에 저장되는 데이터는 항상 키를 가져야 한다
- 데이터에 접근할 때는 키를 이용한다.
```dart
main() {
    Map<String, String> map = {'one': 'first', 'two': 'second'};
}
```