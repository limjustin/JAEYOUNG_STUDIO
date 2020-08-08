# How to use Git in Command

### 지식 공유 해주신 선배님들

* [Dae Hoon](https://github.com/daehoon12) 
* [Handong Kim](https://github.com/201411108) 

<br></br>

### **기본 명령어 정리**

- git init : git 생성하기
  - .git을 확인할 수 있는 방법은 Windows에서는 dir /ah를 사용
  - 이는 숨긴 파일을 볼 수 있게 해주는 명령어
- git remote add origin 레포지토리 주소 : git repository 연동
- git remote -v : git 계정 확인
- git fetch : git 서버에서 최신 코드 받아 오기
- git pull : git 서버에서 최신 코드 받아와 merge 하기
- git status : 현재 상태 확인
- git add 파일 이름 : 파일을 추가하는 작업
- git commit -m "커밋 내용" : 커밋 내용을 추가하는 작업
- git push : 로컬 저장소에 있는 것들을 git으로 올림

<br></br>

### 본격 업로드 과정

1. **작업하고자 하는 디렉토리로 이동**

   ```
   C:\Users\user\Desktop>cd BOJ
   ```

2. **git init을 통해 git 생성해주기**

   ```
   C:\Users\user\Desktop\BOJ>git init
   Initialized empty Git repository in C:/Users/user/Desktop/BOJ/.git/
   ```

3. **git remote add origin 통해 Repository 연결 (git remove -v 통한 계정 확인은 확인용)**

   ```
   C:\Users\user\Desktop\BOJ>git remote add origin https://github.com/limjustin/Algorithm.git
   
   C:\Users\user\Desktop\BOJ>git remote -v
   origin  https://github.com/limjustin/Algorithm.git (fetch)
   origin  https://github.com/limjustin/Algorithm.git (push)
   ```

4. **git fetch 및 git pull로 서버에서 최신 작업물 받아오기**

   ```
   C:\Users\user\Desktop\BOJ>git fetch
   remote: Enumerating objects: 61, done.
   remote: Counting objects: 100% (61/61), done.
   remote: Compressing objects: 100% (55/55), done.
   remote: Total 61 (delta 12), reused 0 (delta 0), pack-reused 0
   Unpacking objects: 100% (61/61), done.
   From https://github.com/limjustin/Algorithm
    * [new branch]      master     -> origin/master
   
   C:\Users\user\Desktop\BOJ>git pull origin master
   From https://github.com/limjustin/Algorithm
    * branch            master     -> FETCH_HEAD
   ```

5. **git status 통해 현재 상태 확인 및 git add를 통해 파일 업로드**

   ```
   C:\Users\user\Desktop\BOJ>git status
   On branch master
   Untracked files:
     (use "git add <file>..." to include in what will be committed)
           BOJ/BOJ_1931_Modify.cpp
           
   
   C:\Users\user\Desktop\BOJ>git add *
   
   C:\Users\user\Desktop\BOJ>git status
   On branch master
   Changes to be committed:
     (use "git restore --staged <file>..." to unstage)
           new file:   BOJ/BOJ_1931_Modify.cpp
   ```

6. **git commit -m "커밋 내용" 통해 커밋 내용 기재**

   ```
   C:\Users\user\Desktop\BOJ>git commit -m "algorithm github upload"
   [master 81ae987] algorithm github upload
    1 file changed, 76 insertions(+)
    create mode 100644 BOJ/BOJ_1931_Modify.cpp
   ```

7. **git push 통해 로컬 저장소에 있는 것들을 git에 업로드**

   ```
   C:\Users\user\Desktop\BOJ>git push origin master
   Enumerating objects: 6, done.
   Counting objects: 100% (6/6), done.
   Delta compression using up to 8 threads
   Compressing objects: 100% (4/4), done.
   Writing objects: 100% (4/4), 1.20 KiB | 245.00 KiB/s, done.
   Total 4 (delta 1), reused 0 (delta 0)
   remote: Resolving deltas: 100% (1/1), completed with 1 local object.
   To https://github.com/limjustin/Algorithm.git
      cc23a75..81ae987  master -> master
   ```