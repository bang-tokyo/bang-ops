環境構築
-------------------------

::

   git clone git@github.com:bang-tokyo/bang-ops.git

接続先設定
-------------------------

$HOME/.ssh/config の設定方法は別途slackなどで確認のこと

ユーザ作成方法
-------------------------

以下のコマンドでユーザ作成を行うことができる

::
   
   # 本番環境の全台に実行する
   ansible-playbook -i production all.yml --ask-sudo-pass

パスワード文字列確認方法
-------------------------

::
   
   openssl passwd -salt bang -1 "設定したいパスワード"