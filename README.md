# tp-coaching-webforce3
Instruction pour la session de coaching
Faire un git clone de ce repo en local dans votre directory c:\projet dans Git-bash
git clone https://github.com/mfettah01/tp-coaching-webforce3.git
Faire un git clone dans la home directorie de votre VM fournie
Mettre à jour les packages de votre VM ubuntu
sudo apt update sudo apt upgrade
Vérifier la version de python3 déjà installée
python3 --version Python 3.8.10
créer un alias nommé python valide pour le user ubuntu de votre VM vérifier en faisant python -V
nano ~/.bashrc saisie alias python='python3' Ctlx Y Entree
pour sauvegarder l'alias source source ~/.bashrc
vérifier en faisant python -V
Python 3.8.10
lancement cmd pip install flask
Command 'pip' not found, but can be installed with:
sudo apt install python3-pip
ubuntu@coaching-5:~/tp-coaching-webforce3$ sudo apt install python3-pip
pip install flask Successfully installed Ji.....
Recherche le disque supplémentaire de 1Gb connecté à la VM
cmd sudo fdisk -l Disk /dev/vdc: 1 GiB
Formattez ce disque au format ext4
sudo mkfs.ext4 /dev/vdc
Monter (mount) ce disque sur le point montage /home/ubuntu/tp-coaching-webforce3/log
mkdir /home/ubuntu/tp-coaching-webforce3/log
sudo mount /dev/vdc /home/ubuntu/tp-coaching-webforce3/log
/dev/vdc        976M  2.6M  907M   1% /home/ubuntu/tp-coaching-webforce3/log
git commit

*** Please tell me who you are.

Run

  git config --global user.email "you@example.com"
  git config --global user.name "Your Name"

git config --global user.email mohamedfettah@hotmail.fr
ubuntu@coaching-5:~/tp-coaching-webforce3$ git config --global user.name mfettah01

git push
Username for 'https://github.com': mfettah01
Password for 'https://mfettah01@github.com': 
git pull
1 file changed, 25 insertions(+)
