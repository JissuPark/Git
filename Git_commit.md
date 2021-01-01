> GIt의 큰 장점중에 하나는 이전에 commit한 기록이 남아 있다면 해당 기록으로 되돌릴 수 있다는 것이다.

## 명령어

------

```
git reset (--option) [Hash|Head~(숫자)]
```

<br>

## 방법

------

1. Commit Hash를 통해 되돌리기
2. HEAD의 상대적 위치를 통해 되돌리기

<br>

### Commit Hash 이용

------

- `git reset [hash]`와 같이 사용한다.

- `git log`를 통해서 볼 수 있는 기록의 Hash를 인자로 준다.

  ```bash
  ~/Desktop/git (main) $ git log
  commit 4103b201936fcc5f6ab1adfca4806798fa9f32bd (HEAD -> main)
  Author: 이름 <이메일>
  Date:   Fri Jan 1 16:48:26 2021 +0900
  
      commit test
  
  commit 99959e51e24b5d492802385290cd3952c6a2bc31 (upstream/main)
  Merge: 3ec1099 aa9e3e6
  Author: JissuPark <qkrwltn9412@gmail.com>
  Date:   Thu Dec 31 01:06:24 2020 +0900
  ```

- `git log --oneline`을 통해 보이는 Hash의 첫 7자리만 넣어줘도 된다.

  ```bash
  ~/Desktop/git (main) $ git log --oneline
  4103b20 (HEAD -> main) commit test
  99959e5 (upstream/main) Merge branch 'main' of <https://github.com/JissuPark/Git> into main
  
  ~/Desktop/git (main) $ git reset 99959e5
  ```

  <br>

### HEAD의 상대적 위치 사용

------

- `git reset HEAD~(숫자)` 와 같이 사용한다.

- `git log`에서 가장 최근 Commit이 HEAD의 위치이다.

  ```bash
  ~/Desktop/git (main) $ git log
  commit 4103b201936fcc5f6ab1adfca4806798fa9f32bd (HEAD -> main)
  Author: 이름 <이메일>
  Date:   Fri Jan 1 16:48:26 2021 +0900
  
      commit test
  ```

- 이 HEAD라는 위치를 기준으로 `~숫자` 를 붙여 돌아가 상대적 위치를 정한다.

  ex) HEAD~1은 HEAD 이전의 Commit, HEAD~2는 HEAD 두개전의 Commit과 같은 순서이다.

  <br>

## 결과 확인

------

- 되돌리고 나면 `git log`와 `git status` 에서 결과를 확인할 수 있다.

  1. `git log --oneline`

     4103b20 hash에 해당하는 Commit이 사라진 것을 볼 수 있다.

     ```bash
     ~/Desktop/git (main) $ git log --oneline
     99959e5 (HEAD -> main, upstream/main) Merge branch 'main' of <https://github.com/JissuPark/Git> into main
     ```

  2. `git status`

     이전 Commit에서 추가했던 파일이 다시 Untracked files에 속해있는 것을 볼 수 있다.

     ```bash
      ~/Desktop/git (main) $ git status
     On branch main
     Untracked files:
       (use "git add <file>..." to include in what will be committed)
             Git_commit.md
     
     nothing added to commit but untracked files present (use "git add" to track)
     ```