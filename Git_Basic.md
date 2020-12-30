# Git 기본 명령어

**github에 레포지토리를 만들고 해당 레포지토리와 연결할 폴더가 전제되어있다. 또한, 일반적인 github 업로드 순서를 따라 작성되었다.**



1. `git init`

   ------

   현재 폴더를 git으로 관리하도록 한다 == 초기화

   실행하면 숨겨진 폴더로 .git 폴더를 볼 수 있다.

   ```bash
   ~/Desktop/git $ git init
   Initialized empty Git repository in C:/Users/qkrwl/Desktop/git/.git/
   
   ~/Desktop/git (main)
   $ ls -al
   total 8
   drwxr-xr-x 1 qkrwl 197609 0 12월 30 21:23 ./
   drwxr-xr-x 1 qkrwl 197609 0 12월 30 21:22 ../
   drwxr-xr-x 1 qkrwl 197609 0 12월 30 21:23 .git/
   ```

   

   

2. `git config`

   ------

   github와 연결을 위한 설정을 한다.

   ```bash
   ~/Desktop/git (main) $ git config --global user.email '이메일'
   ~/Desktop/git (main) $ git config --global user.name '이름'
   ```

   설정한 값을 볼 수도 있다.

   ```bash
   ~/Desktop/git (main) $ git config --global --list
   user.email='이메일'
   user.name='이름'
   ...
   ```

   

   

3. `git add [file|folder]` | `git restore --staged [file|folder]`

   ------

   연결된 레포지토리에 올릴 파일을 추가 | 삭제한다.

   파일명이나 폴더명을 사용해 선택적으로 등록|해제할 수 있다.

   - `git add .` 과 같이 현재 디렉토리 전체를 한번에 등록할 수 있다.

   - 구버전에서는 restore대신 `git reset HEAD [file|folder]` 로 쓴다.

   - 추가

     ```bash
     ~/Desktop/git (main) $ echo 'hello Git world' > sample.txt
     ~/Desktop/git (main) $ ls
     sample.txt
     ~/Desktop/git (main) $ git add sample.txt
     ```

   - 제거

     ```bash
     ~/Desktop/git (main) $ git restore --staged sample.txt
     ~/Desktop/git (main) $ git reset HEAD sample.txt
     ```

   

4. `git status`

   ------

   git이 관리하고 있는 파일과 폴더에 대해서 정보를 표시한다.

   - 추가된 경우

     ```bash
     ~/Desktop/git (main) $ git status
     On branch main
     
     No commits yet
     
     Changes to be committed:
       (use "git rm --cached <file>..." to unstage)
             new file:   sample.txt
     ```

   - 아직 추가되지 않은 경우

     ```bash
     ~/Desktop/git (main) $ git status
     On branch main
     Untracked files:
       (use "git add <file>..." to include in what will be committed)
             temp.txt
     
     nothing added to commit but untracked files present (use "git add" to track)
     ```

   - 수정된 경우

     ```bash
     ~/Desktop/git (main) $ git status
     On branch main
     Changes not staged for commit:
       (use "git add <file>..." to update what will be committed)
       (use "git restore <file>..." to discard changes in working directory)
             modified:   sample.txt
     
     no changes added to commit (use "git add" and/or "git commit -a")
     ```

     ​	

     ​	

5. `git commit -m [message]`

   ------

   `git add/restore`를 통해 추가/삭제된 파일들을 하나의 기록으로 저장한다.

   ```bash
    ~/Desktop/git (main) $ git commit -m '[ADD] sample.txt'
   [main (root-commit) d1d23e4] [ADD] sample.txt
    1 file changed, 1 insertion(+)
    create mode 100644 sample.txt
   ```

   ​	

   ​			

6. `git log (branch)`

   ------

   `git commit`을 통해 남겨진 기록들을 관리한다.

   ```bash
   ~/Desktop/git (main) $ git log
   commit d1d23e4e78e88d82a71a43dad2b3d8b33b2d9a04 (HEAD -> main)
   Author: JissuPark <qkrwltn9412@gmail.com>
   Date:   Wed Dec 30 22:59:50 2020 +0900
   
       [ADD] sample.txt
   ```

   너무 길다면 한 줄로 볼수 있는 옵션을 사용한다. `--oneline`

   ```bash
   ~/Desktop/git (main) $ git log --oneline
   d1d23e4 (HEAD -> main) [ADD] sample.txt
   ```

   전체적인 흐름을 보고 싶다면 그래프 옵션을 사용한다. `--graph`

   해당 옵션은 commit 수가 많고 branch가 있다면 더욱 빛을 발한다.

   ```bash
   ~/Desktop/git (main) $ git log --oneline --graph
   * d1d23e4 (HEAD -> main) [ADD] sample.txt
   ```

   ​		

   ​			

7. `git remote add [repository] [github_url]`

   ------

   원격 레포지토리와 연결을 담당한다.

   ```bash
   ~/Desktop/git (main) $ git remote add upstream <https://github.com/JissuPark/Git.git>
   ```

   `-v` 옵션을 통해 등록된 레포지토리를 확인한다.

   ```bash
   ~/Desktop/git (main) $ git remote -v
   upstream        <https://github.com/JissuPark/Git.git> (fetch)
   upstream        <https://github.com/JissuPark/Git.git> (push)
   ```

   ​		

   ​		

8. `git push [repository] [branch]`

   ------

   [branch]에 commit된 기록과 함께 파일들을 원격 [repository]로 전송한다. == 파일 올리기

   - repository :  `git remote` 를 통해서 설정한 별칭
   - branch : 로컬에서 사용하고 있는 브랜치명

   ```bash
   ~/Desktop/git (main) $ git push upstream main
   Enumerating objects: 3, done.
   Counting objects: 100% (3/3), done.
   Writing objects: 100% (3/3), 243 bytes | 121.00 KiB/s, done.
   Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
   To <https://github.com/JissuPark/Git.git>
    * [new branch]      main -> main
   ```