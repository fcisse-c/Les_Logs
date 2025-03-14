# Les Logs
  
1.Installe un serveur web (Apache ou Nginx) sur une machine virtuelle Linux
🔹 Installation d'Apache :
 ```bash
   sudo apt update
   sudo apt install apache2 -y
   ```


🔹 Installation de Nginx :
 ```bash
  sudo apt update
  sudo apt install nginx -ysudo apt update
  sudo apt install nginx -y
   ```

📝 2. Configuration du logging
Par défaut, les logs sont stockés dans :

Apache : /var/log/apache2/access.log et /var/log/apache2/error.log

Nginx : /var/log/nginx/access.log et /var/log/nginx/error.log

Si besoin, tu peux ajuster la configuration des logs dans :

Apache : /etc/apache2/apache2.conf

Nginx : /etc/nginx/nginx.conf

 3. Génération de trafic
Tu peux utiliser curl pour simuler du trafic :
bash
CopierModifier
curl -s http://localhost > /dev/null

curl -s http://localhost/nonexistentpage > /dev/null

Ou un navigateur en visitant l'IP de la VM.


📊 4. Analyse des logs
🔹 Requêtes réussies (code 200) :
 ```bash
 grep ' 200 ' /var/log/apache2/access.log | wc -l  # Pour Apache
 grep ' 200 ' /var/log/nginx/access.log | wc -l    # Pour Nginx
   ```

![image](https://github.com/user-attachments/assets/d9817421-b6dd-4909-ba52-94daa7435444)


🔹 Erreurs 404 :
 ```bash
grep ' 404 ' /var/log/apache2/access.log | wc -l
grep ' 404 ' /var/log/nginx/access.log | wc -l
   ```

![image](https://github.com/user-attachments/assets/ede8279d-dae0-4d80-95cb-a0f711d6fa2a)

🔹 Adresses IP les plus fréquentes :

![image](https://github.com/user-attachments/assets/563ec48b-129b-4a4a-bff1-a8cb2a63256a)


