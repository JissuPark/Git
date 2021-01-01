## Branch란?

------

- 말그대로 새로운 가지를 치는 것을 의미한다.

- 현재 관리중인 Git에서 새로운 가지를 열어 관리하겠다는 것이다.

  <br>

## Branch 관련 명령어

------

- `git branch` : 브랜치 목록 확인

- `git branch [name]` : [name]이라는 브랜치 생성

- `git switch [name]` : [name]이라는 브랜치로 이동

  구버전 = `git checkout [name]`

- `git switch -c [name]` : [name]이라는 브랜치를 생성하고 이동

  구버전 = `git checkout -b [name]`

- `git branch -d [name]` : [name]이라는 브랜치 삭제

  <br>

## Merge란?

------

- 관리하던 가지를 병합하겠다는 의미이다.

- 각각 서로 다른 브랜치를 하나의 브랜치로 통합하여 관리한다.

  <br>

## Merge 방법

------

Merge는 `git merge [branch]`와 같은 명령으로 동작하고 총 3가지 방법으로 나뉜다.

1. Fast-Forward

2. 3-way Merge

3. Merge Conflict

   <br>

   ### Fast-Forward

   ------

   - branch 중 하나가 수정사항이 없는 경우

   - 단순히 합치면 되기때문에 충돌 가능성이 없다.

     ex) main에 login을 합치는 경우

     ```bash
     (main) $ git merge login
     Updating 97d7e0c..6398897
     Fast-forward
      login.txt | 0
      1 file changed, 0 insertions(+), 0 deletions(-)
      create mode 100644 login.txt
     ```

     <br>

   ### 3way Merge

   ------

   - 서로 수정한 파일이 겹치지 않을 경우

   - 자동으로 기록을 위한 커밋이 생성된다.

     ex) main에 logout을 합치는 경우

     ```bash
     (main) $ git merge logout
     hint: Waiting for your editor to close the file...
     [main 2020-12-30T07:26:29.469Z] update#setState idle
     [main 2020-12-30T07:26:59.480Z] update#setState checking for updates
     [main 2020-12-30T07:26:59.636Z] update#setState idle
     Merge made by the 'recursive' strategy.
      logout.txt | 0
      1 file changed, 0 insertions(+), 0 deletions(-)
      create mode 100644 logout.txt
     ```

     <br>

   ### Merge Comflict

   ------

   - 실제로 같은 파일에 대해 충돌이 일어난 경우

   - 합의를 위한 커밋이 필요하다.

     ex) main에 signup을 합치다 [Readme.md](http://readme.md) 파일에 충돌발생

     ```bash
     (main) $ git merge signup
     Auto-merging Readme.md
     CONFLICT (content): Merge conflict in Readme.md
     Automatic merge failed; fix conflicts and then commit the result.
     ```

   - 직접 코드를 수정해야한다.

     (위에 ~~변경사항수락을 통해서 수정해도 됨)

     ```bash
     	$ code Readme.md
     ```

     ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e87d5999-cefc-4fc7-b996-d03f0ddd9763/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e87d5999-cefc-4fc7-b996-d03f0ddd9763/Untitled.png)

   - 수정 후에는 커밋을 새로 생성해줘야 제대로 완료된다.

     ```bash
     $ git add . 
     $ git commit -m 'Fix Conflict'
     ```

     <br>

## Merge 규칙

------

- 머지는 main/master가 수행해야한다.

- 머지가 완료된 브랜치는 삭제한다.

  ```bash
  $ git branch -d login
  Deleted branch login (was 6398897).
  ```