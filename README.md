# Les Logs
🚀 1. Installation d’un serveur web (Apache ou Nginx)
🔹 Installation d'Apache :
bash
CopierModifier
sudo apt update
sudo apt install apache2 -y

🔹 Installation de Nginx :
bash
CopierModifier
sudo apt update
sudo apt install nginx -y

Ensuite, vérifie si le service fonctionne :
bash
CopierModifier
sudo systemctl status apache2  # Pour Apache
sudo systemctl status nginx    # Pour Nginx


📝 2. Configuration du logging
Par défaut, les logs sont stockés dans :
Apache : /var/log/apache2/access.log et /var/log/apache2/error.log
Nginx : /var/log/nginx/access.log et /var/log/nginx/error.log
Si besoin, tu peux ajuster la configuration des logs dans :
Apache : /etc/apache2/apache2.conf
Nginx : /etc/nginx/nginx.conf

🔥 3. Génération de trafic
Tu peux utiliser curl pour simuler du trafic :
bash
CopierModifier
curl -s http://localhost > /dev/null
curl -s http://localhost/nonexistentpage > /dev/null

Ou un navigateur en visitant l'IP de la VM.

📊 4. Analyse des logs
🔹 Requêtes réussies (code 200) :
bash
CopierModifier
grep ' 200 ' /var/log/apache2/access.log | wc -l  # Pour Apache
grep ' 200 ' /var/log/nginx/access.log | wc -l    # Pour Nginx

🔹 Erreurs 404 :
bash
CopierModifier
grep ' 404 ' /var/log/apache2/access.log | wc -l
grep ' 404 ' /var/log/nginx/access.log | wc -l

🔹 Adresses IP les plus fréquentes :
bash
CopierModifier
awk '{print $1}' /var/log/apache2/access.log | sort | uniq -c | sort -nr | head -10
awk '{print $1}' /var/log/nginx/access.log | sort | uniq -c | sort -nr | head -10
