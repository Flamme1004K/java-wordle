# 미션 - 워들

## 🔍 진행 방식

- 미션은 **기능 요구 사항, 프로그래밍 요구 사항, 과제 진행 요구 사항** 세 가지로 구성되어 있다.
- 세 개의 요구 사항을 만족하기 위해 노력한다. 특히 기능을 구현하기 전에 기능 목록을 만들고, 기능 단위로 커밋 하는 방식으로 진행한다.
- 기능 요구 사항에 기재되지 않은 내용은 스스로 판단하여 구현한다.

## 🚀 기능 요구 사항

선풍적인 인기를 끌었던 영어 단어 맞추기 게임이다.

- 6x5 격자를 통해서 5글자 단어를 6번 만에 추측한다.
- 플레이어가 답안을 제출하면 프로그램이 정답과 제출된 단어의 각 알파벳 종류와 위치를 비교해 판별한다.
- 판별 결과는 흰색의 타일이 세 가지 색(초록색/노란색/회색) 중 하나로 바뀌면서 표현된다.
    - 맞는 글자는 초록색, 위치가 틀리면 노란색, 없으면 회색
    - 두 개의 동일한 문자를 입력하고 그중 하나가 회색으로 표시되면 해당 문자 중 하나만 최종 단어에 나타난다.
- 정답과 답안은 `words.txt`에 존재하는 단어여야 한다.
- 정답은 매일 바뀌며 ((현재 날짜 - 2021년 6월 19일) % 배열의 크기) 번째의 단어이다.

### 입출력 요구 사항

#### 실행 결과 예시

```light
WORDLE을 6번 만에 맞춰 보세요.
시도의 결과는 타일의 색 변화로 나타납니다.
정답을 입력해 주세요.
hello

⬜⬜🟨🟩⬜

정답을 입력해 주세요.
label

⬜⬜🟨🟩⬜
🟨⬜⬜⬜🟩

정답을 입력해 주세요.
spell

⬜⬜🟨🟩⬜
🟨⬜⬜⬜🟩
🟩🟩⬜🟩🟩

정답을 입력해 주세요.
spill

4/6

⬜⬜🟨🟩⬜
🟨⬜⬜⬜🟩
🟩🟩⬜🟩🟩
🟩🟩🟩🟩🟩
```

---

## 🎯 프로그래밍 요구 사항

- JDK 11 버전에서 실행 가능해야 한다. **JDK 11에서 정상적으로 동작하지 않을 경우 0점 처리한다.**
- 프로그램 실행의 시작점은 `Application`의 `main()`이다.
- [Java 코드 컨벤션](https://github.com/woowacourse/woowacourse-docs/tree/master/styleguide/java) 가이드를 준수하며 프로그래밍한다.
- 프로그래밍 요구 사항에서 별도의 변경 불가 안내가 없는 한 자유롭게 파일을 수정하고 패키지를 이동할 수 있다.
- indent(인덴트, 들여쓰기) depth를 3이 넘지 않도록 구현한다. 2까지만 허용한다.
    - 예를 들어 while문 안에 if문이 있으면 들여쓰기는 2이다.
    - 힌트: indent(인덴트, 들여쓰기) depth를 줄이는 좋은 방법은 함수(또는 메서드)를 분리하면 된다.
- 3항 연산자를 쓰지 않는다.
- 함수(또는 메서드)의 길이가 15라인을 넘어가지 않도록 구현한다.
    - 함수(또는 메서드)가 한 가지 일만 잘 하도록 구현한다.
- else 예약어를 쓰지 않는다.
    - 힌트: if 조건절에서 값을 return하는 방식으로 구현하면 else를 사용하지 않아도 된다.
    - else를 쓰지 말라고 하니 switch/case로 구현하는 경우가 있는데 switch/case도 허용하지 않는다.


---
## 워들 도메인에 대한 요구 사항
- . 일단 확정
- ? 아직 모름 애매...

- [x] 하나의 글자는 Letter 이다. (Letter class)
    - [x] Letter는 영문자이어야 한다.
- [x] 영어 단어는 Letters 이다. (Letters class)
    - [x] 영단어야만 한다. 
    - [x] 여러 개의 Letter는 Letters 이다.
    - [x] Letters는 5글자로 이루어져 있다.
- [ ] 오늘의 정답은 Answer 가 가지고 있다.  (Answer class)
    - [ ] Answer의 정답은 Game이 준다?
    - [ ] Answer는 제출된 단어를 비교 할 수 있다.
- [ ] 정답과 답안에 대한 상태는 LetterResult 이다. (LetterResult enum class)
    - [ ] 상태는 GREEN / YELLOW / GRAY 를 가지고 있다.
    - [ ] GREEN : 정답 글자와 위치가 같은 경우.
    - [ ] YELLOW : 정답 글자는 맞지만, 위치가 다른 경우.
    - [ ] GRAY : 정답 글자도 안맞고, 위치도 다른 경우.
    - [ ] 예외 : 두 개의 동일한 문자를 입력하고 그중 하나가 회색으로 표시되면 해당 문자 중 하나만 최종 단어에 나타난다.
- [ ] 정답과 답안을 비교한 결과는 LetterResults가 가지고 있다. (LetterResults class)
    - [ ] LetterResults는 6개의 결과만 가지고 있을 수 있다.
- [ ] 정답과 답안은 `words.txt`에 존재하는 단어여야한다.
    - [ ] Words에는 정답과 답안 리스트가 들어가 있다.
- [ ] 정답은 매일 바뀌며 ((현재 날짜 - 2021년 6월 19일) % 배열의 크기) 번째의 단어이다.

---
## 뷰에 대한 요구 사항

---