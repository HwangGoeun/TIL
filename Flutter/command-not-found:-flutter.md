# command not found: flutter

1. 터미널을 열고 `~/.zshrc` 파일을 연다.
2. `PATH="$PATH:[플러터 SDK 파일 경로]/flutter/bin"` 를 입력한다.<br>
    2-1. 만약 SDK 파일이 어디있는지 모르겠다면 [이 링크](https://docs.flutter.dev/get-started/install)에 접속해 SDK 파일을 다운받는다.
3. `source ~/.zshrc`를 입력해 수정 사항을 적용한다.
4. `flutter doctor` 명령어를 통해 제대로 적용되었는지 확인한다.