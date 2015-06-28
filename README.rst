環境構築
-------------------------

submoduleを使っているため、clone後にsubmodule情報取得する必要あり

::

   git clone git@github.com:bang-tokyo/bang-ops.git
   git submodule update --init --recursive

bang-server開発環境構築
-------------------------

::

   # vagrant起動
   vagrant up
   
   # 初回実行
   ansible-playbook -i hosts/vagrant development.yml --user=vagrant --private-key=~/.vagrant.d/insecure_private_key
   ## TODO: root/vagrant のauthorized_keysを消す

   # 2回目以降($USERは自分のユーザ、ssh-configに記載あれば指定の必要なし)
   ansible-playbook -i hosts/vagrant development.yml --ask-sudo-pass --user=$USER 

接続先設定
-------------------------

$HOME/.ssh/config の設定方法は別途slackなどで確認のこと

ユーザ作成方法
-------------------------

以下のコマンドでユーザ作成を行うことができる

::
   
   # 本番環境の全台に実行する
   ansible-playbook -i hosts init.yml --ask-sudo-pass

パスワード文字列確認方法
-------------------------

::
   
   openssl passwd -salt bang -1 "設定したいパスワード"

ansible memo
-------------------------

::

   # rootと表示される
   ansible --user=root --private-key=~/.ssh/id_rsa.bang.rootkey1 -i hosts bang-gw01 -a "whoami"
   
   # ssh-configなどで設定しているユーザ名になる
   ansible -i hosts bang-gw01 -a "whoami"

   # nopass sudo userじゃないとエラーになる
   ansible -i hosts bang-gw01 --sudo -a "whoami"

   # sudoで実行されるのでrootとなる、実行前にrootのパスワードがpromptで聞かれる
   ansible -i hosts bang-gw01 --sudo --ask-sudo-pass -a "whoami"

   # 
   # rootユーザで、user/groupの初期化する
   #
   ansible --user=root --private-key=~/.ssh/id_rsa.bang.rootkey1 -i hosts bang-gw01 -a "echo 'initialize!'"
   
   # 
   # sudo付きユーザで、user/groupの初期化する
   #
   ansible -i hosts bang-gw01 -a "echo 'initialize!'"
   
   # 
   # sudo付きユーザで、rootのid_rsaを消す
   #
   ansible -i hosts bang-gw01 -a "echo 'clear root identity'"

- my.cnf
- ansible-vault
- ImageMagick
- 開発ルール

  - vm内でgit cloneして、vmにsshして開発する
  - 反映もvmから = .ssh/configが必要

- いらないこと

  - apache install

- 疑問

  - nodejsは何のため？

