# ベースイメージの指定
FROM almalinux

LABEL mainter="user" \
      version="v0.1"

RUN dnf update -y && dnf install -y stress-ng

# app_userの追加
RUN useradd -m app_user
# app_userに切り替え
USER app_user

# test1.txtファイルの作成
#RUN touch test1.txt
# 作業ディレクトリの作成
WORKDIR /app
# test2.txtファイルの作成
RUN touch test2.txt

# カレントディレクトリのsample.txtファイルを追加
COPY --chown=app_user:app_user sample.txt ./
# dirディレクトリを追加
COPY --chown=app_user:app_user dir ./

# 環境変数の設定
ENV SAMPLE=value
# KEYの値を出力
RUN echo "SAMPLE=$SAMPLE"

# 起動引数の設定
ARG ARG_SAMPLE1
ARG ARG_SAMPLE2=default_value

RUN echo "ARG_SAMPLE1=$ARG_SAMPLE1"
RUN echo "ARG_SAMPLE2=$ARG_SAMPLE2"

# カレントディレクトリの表示
CMD ["ls","-l"]