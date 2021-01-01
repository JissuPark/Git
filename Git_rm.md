> github에 올리길 원치 않는 파일을 올렸을 경우, 삭제할 수 있는 방법

원활한 설명을 위해 `secret`이라는 파일을 생성해 잘못 올렸다고 가정하자.

1. 파일 생성

   ```bash
   ~/Desktop/git (main) $ touch secret
   ```

2. Git에 추가

   ```bash
   ~/Desktop/git (main) $ git add .
   ~/Desktop/git (main) $ git status
   On branch main
   Changes to be committed:
     (use "git restore --staged <file>..." to unstage)
           new file:   secret
   ```

3. Commit

   ```bash
   ~/Desktop/git (main) $ git commit -m 'fault'
   [main 56f3e17] fault
    1 file changed, 0 insertions(+), 0 deletions(-)
    create mode 100644 secret
   ```

4. github에 업로드

   ```bash
   ~/Desktop/git (main) $ git push upstream main
   ```

그럼 이제  `secret`파일이 github에 올라가있는 상황이 되었다.

여기서 파일을 삭제하려면 먼저 원격 저장소에 있는 파일을 관리하지 않도록 제외시켜준 뒤 재업로드 해주면 된다.

순서대로설명하자면,

1. 먼저 `.gitignore` 파일에 추가하여 실수로 올라가는 일이 생기지 않게 한다. (선택사항이지만 권장하는 방법)

2. `git rm --cached [file]`을 통해서 더이상 관리하지 않도록 제외시켜준다.

   ```bash
   ~/Desktop/git (main) $ git rm --cached secret
   rm 'secret'
   
   ~/Desktop/git (main) $ git status
   On branch main
   Changes to be committed:
     (use "git restore --staged <file>..." to unstage)
           deleted:    secret
   ```

3. Commit 후 재 업로드해준다.

   ```bash
   ~/Desktop/git (main) $ git commit -m 'fix fault'
   [main eb2e04d] fix fault
    1 file changed, 0 insertions(+), 0 deletions(-)
    delete mode 100644 secret
   
   ~/Desktop/git (main) $ git push upstream main
   ```

4. 이제 github에서 파일이 삭제되었음을 확인할 수 있다.

------

**파일이 삭제되어도 Commit 기록은 남기때문에 해당 기록을 보면 파일을 볼 수 있다. 그러니 처음부터 올라가지 않도록 gitignore 작성을 습관화하자.**