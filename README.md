# Docker example

```dockerfile
FROM openjdk:8-jdk-alpine
ARG JAR_FILE=target/*.jar
COPY ${JAR_FILE} app.jar
ENTRYPOINT ["java", "-jar", "/app.jar"]
```

## dockerfile build
- docker build --build-arg JAR_FILE=build/libs/*.jar -t 이미지명 .

## run
- docker run -d -p 80:8080 --name 컨테이너명 이미지명

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
