# 서버에 올리는 방법

## Pre
이 절차는 딱 한번만 제대로 하면 된다.
```bash
docker-compose up setup
```

### 제대로 실행되었는지 확인하는 법
```bash
docker ps -a --format 'table {{.Names}}\t{{.Image}}\t{{.Status}}' | grep setup
```
위 명령어를 실행해서, 

![Alt text](image/image01.png)

`Exited(0)`가 확인되면 정상 실행 완료!

## `.env` 파일 작성
`.env.exmaple` 파일을 만들어서, `.env` 파일은 git에 올라가지 않도록 수정했다! 

### 1. 비밀번호 초기화
```bash
$ docker-compose exec elasticsearch bin/elasticsearch-reset-password --batch --user elastic
```

일단 엘라스틱서치만 사용하기 때문에 `elastic` 유저 비밀번호만 초기화해준다.

위 커맨드를 실행하면,
```
Password for the [elastic] user successfully reset.
New value: (새로운 비밀번호)
```
예시같은 텍스트가 출력되는데, 새로운 비밀번호 값을 복사하자. `ELASTIC_PASSWORD`에 들어갈 값

### 2. `.env` 파일 생성
`.env.example` 파일을 복사해서, `.env` 파일을 만들자.

`# change this` 주석이 달린,
* `ELASTIC_PASSWORD`
* `DB_NAME`
* `DB_USERNAME`
* `DB_PASSWORD`

4가지 항목을 채워주자.

## 실행
```shell
$ docker-compose up -d
```