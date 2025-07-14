FROM maven:3.9.9-eclipse-temurin-21 AS builder

# 作業ディレクトリの作成
WORKDIR /app
# demoを/appにコピー
COPY ./demo .
# mavenビルド
RUN mvn package -DskipTests=true

# アプリケーション実行
#CMD ["java","-jar","/app/target/demo-0.0.1-SNAPSHOT.jar"]

# 実行環境
FROM amazoncorretto:21-alpine3.21 AS production

WORKDIR /app
COPY --from=builder /app/target/demo-0.0.1-SNAPSHOT.jar .

CMD ["java","-jar","/app/demo-0.0.1-SNAPSHOT.jar"]