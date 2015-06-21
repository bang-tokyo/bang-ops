接続先設定
-------------------------

$HOME/.ssh/config の設定方法は別途slackなどで確認のこと

ユーザ作成方法
-------------------------

以下のコマンドでユーザ作成を行うことができる

::
   
   ansible-playbook -i hosts users.yml

users.yml内のパスワード部分は以下のコマンドで出力される文字列を使用すること

::
   
   openssl passwd -salt bang -1 "設定したいパスワード"
