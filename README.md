# Docker example

```dockerfile
FROM openjdk:8-jdk-alpine
ARG JAR_FILE=target/*.jar
COPY ${JAR_FILE} app.jar
ENTRYPOINT ["java", "-jar", "/app.jar"]
```

```dockerfile
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
COPY bin/Release/netcoreapp3.1/publish/ App/
WORKDIR /App
ENTRYPOINT ["dotnet", "NetCore.Docker.dll"]
```

- FROM 키워드: 정규화된 Docker 컨테이너 이미지 이름
- COPY: 지정된 폴더를 컨테이너의 폴더에 복사
- WORKDIR: 컨테이너 내부의 현재 디렉터리를 App으로 변경
- ENTRYPOINT: 테이너가 실행 파일로 실행되게 컨테이너를 구성하



## dockerfile build
- docker build --build-arg JAR_FILE=build/libs/*.jar -t 이미지명 .

## 이미지->컨테이너
- docker run -d -p 80:8080 --name 컨테이너명 이미지명


- docker run [OPTIONS] IMAGE[:TAG|@DIGEST] [COMMAND] [ARG....]

| 옵션  | 설명                                                        |
| ----- | ---------------------------------------------------------- |
| -d    | detached mode 흔히 말하는 백그라운드 모드                    |
| -p    | 호스트와 컨테이너의 포트를 연결 (포워딩)                      |
| -v    | 호스트와 컨테이너의 디렉토리를 연결 (마운트)                  |
| -e    | 컨테이너 내에서 사용할 환경변수 설정                         |
| –-name | 컨테이너 이름 설정                                          |
| –rm   | 프로세스 종료시 컨테이너 자동 제거                           |
| -i   | 표준입력(stdin)을 활성화 및 컨테이너 연결 없이도 표준입력 유지  |
| -t   | Bash 사용을 위한 명령어 셀 표시를 위해서 사용함.               |
| -it   | -i와 -t를 동시에 사용한 것으로 터미널 입력을 위한 옵션        |
| –link | 컨테이너 연결 [컨테이너명:별칭]                              |
| –cap-add | cgroups얻는 것                                          |


## 실행/종료
- docker start 컨테이너명
- docker stop 컨테이너명
-  `전부 종료 : docker stop $(docker ps -a -q)`

## 연결
- docker exec -it 컨테이너명 실행할프로세스
- docker attach 컨테이너명

## 컨테이너 목록
- docker ps -a

## Docker 로그인
- docker login -U 

## Docker Hub에 push/pull
- docker push 이미지명
- docker pull 이미지명

## Docker Compose
