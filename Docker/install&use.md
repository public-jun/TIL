# Install & Use

## DockerHubの登録

Docker Desktopをダウンロードするために登録する
ggったらいくらでも方法出てきた

## Docker HubからDocker imageをpull

コンテナはDocker imageから作られる

* Docker imageとは,,,コンテナを作るための元となるもので、携帯ができる.Docker Hubに保存されているのもDocker imageです。使いたいコンテナがあればまず __Docker 
  imageを手に入れてそれを実行してからコンテナを作る__
  
* Docker fileとは,,, __ただのTextファイルで，Docker imageを作るための設計書__ です。Docker fileを使わなくても，コンテナ内で新しいパッケージをインストール


>$ docker login

>Login with your Docker ID to push and pull images from Docker Hub. If you don't have a Docker ID, head over to https://hub.docker.com to create one.

>Username:

* UsernameとPasswordを入力する

* Dockeer imageをpullする。 pullをするコマンドは $docker pull {IMAGE名:TAG名} です。
このTAGというのはDocker imageのバージョンのようなもの

>$ docker pull hello-world:latest

> library中のあるレジストからtagのものをpullしてくる。IDも記載

* ログイン状態でpullするとDockerは指定されたIMAGE名のレジストリを __Docker Hubからpull__ してくる

>$ docker images

>REPOSITORY TAG IMAGE ID CREATED SIZE

>hello-world latest fce289e99eb9 12 months ago 1.84kB

* $ docker imagesで手元にあるDocker imageのリストを確認できる


## Docker imageからコンテナを作成しよう

 __Docker imageはコンテナのもと__
 
 >$docker run hello-world
 
 * $docker run {IMAGE名} でrunできます．（同じDocker imageがある場合はTAG名をつけます．{IMAGE名:TAG名}という感じで）
 
 * hello-worldというコンテナが実行され，その実行の結果(テキスト出力)が出力される.
 
 * hello-worldのDocker imageには __テキストを出力するという命令があらかじめ設計書に書かれていて，
 コンテナを作成した時にその命令が実行され，テキストが出力された__
 
>$ docker ps -a
  
>CONTAINER ID IMAGE COMMAND CREATED STATUS PORTS NAMES

>a5e307691162 hello-world "/hello" 14 minutes ago Exited (0) 14 minutes ago sharp_dewdney

* コンテナの一覧は $ docker ps -a で確認する(active　ではないもの)。　$docker ps (activeのものを確認)

* 普通にDocker imageをrun(optionを付けずに)をすると， __コンテナ作成(run)⇨コンテナをexitという流れ__ になり、作成後にコンテナを抜けている

* コンテナを出ずにコンテナ内に入るには $docker run -it {IMAGE名:TAG名} bash を実行
-itというoptionは，コンテナ内でTerminal上にきちんと出力などを表示させたり入力できるようにしたりするいわば「Interactionを可能にする」もの

>$ docker run -it hello-world bash

>docker: Error response from daemon: OCI runtime create failed: container_linux.go:348
: starting container process caused "exec: \"bash\": executable file not found in $PATH": unknown.

* hello-worldのコンテナにはubutuが入っていないので，そもそもbashできない
