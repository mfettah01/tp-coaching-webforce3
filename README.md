# tp-coaching-webforce3

# Exercice 1 Scrum
Instruction pour la session de coaching
Faire un git clone de ce repo en local dans votre directory c:\projet dans Git-bash

 `git clone https://github.com/mfettah01/tp-coaching-webforce3.git`

Faire un git clone dans la home directorie de votre VM fournie

# Exercice 2 - Linux
Mettre à jour les packages de votre VM ubuntu

`sudo apt update sudo apt upgrade`

Vérifier la version de python3 déjà installée

`python3 --version` Python 3.8.10

créer un alias nommé python valide pour le user ubuntu de votre VM vérifier en faisant python -V

saisie alias 

`nano ~/.bashrc`  
python='python3' Ctlx Y Entree 

`source ~/.bashrc`

vérifier en faisant 

`python -V`
Python 3.8.10

Faire un pip install flask , suivre les instructions pour installer pip si nécessaire

`sudo apt install python3-pip`
pip install flask Successfully installed Ji.

# Exercice 3 - Storage
Recherche le disque supplémentaire de 1Gb connecté à la VM

`sudo fdisk -l` Disk /dev/vdc: 1 GiB

Formattez ce disque au format ext4

`sudo mkfs.ext4 /dev/vdc`

Monter (mount) ce disque sur le point montage /home/ubuntu/tp-coaching-webforce3/log

`mkdir /home/ubuntu/tp-coaching-webforce3/log`

`sudo mount /dev/vdc /home/ubuntu/tp-coaching-webforce3/log`

/dev/vdc        976M  2.6M  907M   1% /home/ubuntu/tp-coaching-webforce3/log

# Exercice 4 - Git/Github
Dans PyCharm allez dans File->Settings->Version control->github
Appuyer sur la croix, en haut a gauche de cette fenetre et selectionnez log in with token.
entrez votre token github

![Capture d’écran tp 3](https://user-images.githubusercontent.com/122970879/222713953-afdf1313-6691-4db3-b448-12405d4155d2.png)

Vous pouvez maintenant faire des git commit et git push depuis PyCharm

Faire régulierement des commit/push 

`git commit`
*** Please tell me who you are.

`git config --global user.email mohamedfettah@hotmail.fr`

`git config --global user.name mfettah01`

`git push`

Username for 'https://github.com': mfettah01
Password for 'https://mfettah01@github.com': token

`git pull`

1 file changed, 25 insertions(+)

# Exercice 5 - Python

Créez un fichier blogs.py

`nano blogs.py`

Copier le script python suivant ctlc + ctlv

Avec l'aide de la documentation Flask, et de la documentation Python mettre des commentaires dans ce script.

```python
from flask import Flask
import logging
 # create the app
 # app est une application Flask
app = Flask(__name__)
 #effecture la configuration de base du système du journalisation dans la fiche "log/record.log" 
logging.basicConfig(filename='log/record.log', level=logging.DEBUG, format=f'%(asctime)s %(levelname)s %(name)s %(threadName)s : %(message)s')
 # application route, décorateur pour lier une fonction à une URL
@app.route('/blogs')
#creation de la fonction avec le nom blog qui retourne " Welcom to the Blog"
def blog():
    app.logger.info('Info level log')
    app.logger.warning('Warning level log')
    return f"Welcome to the Blog"
 #l'exectuion de l'application en localhost
app.run(host='localhost', debug=True)
```

installation du flask avec le `sudo apt install flask`

Ajouter une variable d'environnement FLASK_APP=blogs , 
mettre cette variable dans le fichier ~/.bashrc de votre user ubuntu
`nano ~/.bashrc` 
saisie du FLASK_APP=blogs dans le fichier

Lancer le web server avec la commande 

`flask run --host=0.0.0.0 -p 30101`

Changement droit avec la comande 

`sudo chmod 777 log/`

dans nano blogs.py inserer if __name__ == '__main__': tabulation pour  app.run(host='localhost', debug=True)

Vérifier avec votre navigateur en utilisant l'url http://<ip_de_votre_vm>:30101/blogs

http://170.75.160.140:30101/blogs
![Capture d’écran tp](https://user-images.githubusercontent.com/122970879/222707974-eb1891a9-7037-4f3c-b49f-42d0ba7862ca.png)

Vérifier que le fichier record.log existe bien dans la directory log

![Capture d’écran tp 2](https://user-images.githubusercontent.com/122970879/222708767-793442bd-b588-47f8-b263-fea08677d3ed.png)

# Exercice 6 - Pare-feu
Trouvez la commande de gestion du firewall sous ubuntu 20.04 Exemple : et Vérifier l'application Web sur ces ports

`sudo ufw status`
Status: inactive

`sudo ufw enable`
Command may disrupt existing ssh connections. Proceed with operation (y|n)? y
Firewall is active and enabled on system startup

`sudo ufw status`
Status: active

fermer le port 5000
`sudo ufw deny 5000`

autoriser le port 30101 
`sudo ufw allow 30101`

`sudo ufw status`
Status: active

To                         Action      From
--                         ------      ----
5000                       DENY        Anywhere                  
30101                      ALLOW       Anywhere                  
5000 (v6)                  DENY        Anywhere (v6)             
30101 (v6)                 ALLOW       Anywhere (v6)
