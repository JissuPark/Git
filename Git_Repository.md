# Git - 레포지토리를 연결하는 두가지 방법 

로컬에 있는 폴더와 github 원격 레포지토리를 연결하는 방식은 크게 두가지가 있다.

1. `git init` & `git remote`

   ------

   - `git init`으로 폴더를 초기화한다.
   - `git remote add [repository] [url]`을 통해서 연결한다.  

   <br>

2. `git clone [git_url]`

   ------

   - 원격 레포지토리에 있는 `[git_url]`을 통해 복제한다.

     ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/e7cd6b2f-72a3-42f6-a0ab-f6ff0202ead2/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20201230%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20201230T154635Z&X-Amz-Expires=86400&X-Amz-Signature=7a5c0adbf0eb5349c98ff3bda3fda33001e7b39fda73577a86174052156db240&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)

     git_url 위치

   - 파일이 있다면 함께 받아온다.

     ```bash
     ~/Desktop/git_temp $ git clone <https://github.com/JissuPark/Git.git>
     Cloning into 'Git'...
     remote: Enumerating objects: 26, done.
     remote: Counting objects: 100% (26/26), done.
     remote: Compressing objects: 100% (14/14), done.
     remote: Total 26 (delta 6), reused 13 (delta 2), pack-reused 0
     Receiving objects: 100% (26/26), 5.84 KiB | 996.00 KiB/s, done.
     Resolving deltas: 100% (6/6), done.
     ```

<br>

처음 Git을 사용한다면 당연히 1번 방법부터 사용할 것이다.

하지만 조금 사용하다보면 1번 방법을 사용할 일이 많지 않다는 것을 느낄 것이다. (나도 얼마 안써봐서 사실 잘 모른다; 그냥 2번이 더 편하다)
