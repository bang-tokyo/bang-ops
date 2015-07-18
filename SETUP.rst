::
   
  openssl passwd -1 "設定したいパスワード"
  
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

- ansible vault
- my.cnf
- mysql datadir
- mysql_install_dbを何回も起動してOK？
- mysql 5.6
- ansible-vault
- 何をtasks/handlers/playbookにするか

  - dev_mine
  - dev_web

    - nginx
    - rbenv

  - dev_db

    - mysql

  - prod_alpha
  - prod_beta
  - prod_db
  - prod_web
