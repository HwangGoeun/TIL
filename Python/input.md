# input
<br>

- 한 줄 단위 문자열 입력<br>
`input()`

<br>

- 문자열이 아닌 다른 자료형으로 입력 받기<br>
`int(input())`<br>
`float(input())`

<br>

- 문자열을 나눠서 입력 받기<br>
    >input() 함수와 split() 함수를 같이 이어 쓰면 입력 받은 문자열을 나누어 리스트로 저장할 수 있다.
    <br>

    - split()을 그대로 사용하면 공백을 기준으로 문자열을 나누어 입력 받는다.<br>
    `input().split()`<br>

    - split() 함수 안에 다른 문자를 넣으면 공백 대신 그 문자를 기준으로 문자열을 자른다.<br>
    `input().split(".")`