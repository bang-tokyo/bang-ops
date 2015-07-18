1. ops環境構築
-------------------------------

::

   git clone git@github.com:bang-tokyo/bang-ops.git
   ansible-galaxy install zzet.rbenv

2. ssh config
-------------------------

$HOME/.ssh/config 例

$(USERNAME)は自分のものに置き換える

::

   Host bang-dev01
     HostName 192.168.33.10
     StrictHostKeyChecking no
     UserKnownHostsFile /dev/null
   
   Host bang-*
     User $(USERNAME)
   
   Host *
     ForwardAgent yes

3. bang-server開発環境構築
-------------------------------

::

   # vagrant起動
   vagrant up
   
   # 初回実行
   ansible-playbook -i hosts/vagrant development.yml --user=vagrant --private-key=~/.vagrant.d/insecure_private_key

   # 2回目以降
   ansible-playbook -i hosts/vagrant development.yml --ask-sudo-pass

4. HOSTS設定
-------------------------

::

   # APIサーバ用hostname
   192.168.33.10  api.localhost.local

5. ssh login
-------------------------

::

   ssh bang-dev01

でログイン可能

後は VM内で git clone して好きに開発する

本番サーバの $HOME/.ssh/config の設定方法は別途slackなどで確認のこと
