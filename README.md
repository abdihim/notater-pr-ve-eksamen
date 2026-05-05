# notater-pr-ve-eksamen
📄 Notater – Flask + Database (enkelt)
🔹 Starte prosjekt
python app.py
🔹 SSH til server
ssh brukernavn@10.2.2.93
🔹 Logge inn i database
mariadb -u abdi -p
🔹 Viktige SQL-kommandoer
SHOW DATABASES;
USE skjema_db;
SHOW TABLES;

SELECT * FROM brukere;
🔹 Lage tabell (hvis nødvendig)
CREATE TABLE brukere (
 id INT AUTO_INCREMENT PRIMARY KEY,
 username VARCHAR(50),
 password VARCHAR(50)
);
🔹 Enkel databasekobling (Python)
import mysql.connector

conn = mysql.connector.connect(
    host="10.2.2.93",
    user="abdi",
    password="abdisemed08",
    database="skjema_db"
)

cursor = conn.cursor()
🔹 Hente data fra skjema
username = request.form["username"]
password = request.form["password"]
🔹 Lagre data (INSERT)
sql = "INSERT INTO brukere (username, password) VALUES (%s, %s)"
cursor.execute(sql, (username, password))
conn.commit()
🔹 Sjekke login (SELECT)
sql = "SELECT * FROM brukere WHERE username=%s AND password=%s"
cursor.execute(sql, (username, password))

result = cursor.fetchone()
🔹 Sjekke resultat
if result:
    return "Riktig login"
else:
    return "Feil login"
🔹 Vise data
cursor.execute("SELECT * FROM brukere")
data = cursor.fetchall()
return str(data)
🔹 Enkel HTML
<form action="/login" method="POST">
  <input type="text" name="username">
  <input type="password" name="password">
  <button type="submit">Logg inn</button>
</form>
🔹 Drift
sudo ufw status
systemctl status mariadb
🔹 GitHub
git init
git add .
git commit -m "update"
git push














ls          # viser filer i mappen
cd mappenavn    # går inn i mappe
cd ..       # går tilbake
mkdir navn  # lager ny mappe
pwd         # viser hvor du er
Server
ssh abdi@10.2.2.93          # logger inn på server
systemctl status mariadb    # sjekker at database kjører
sudo ufw status             # sjekker porter
sudo systemctl restart mariadb  # restarter database
MariaDB
mariadb -u abdi -p          # logger inn i database
SHOW DATABASES;
CREATE DATABASE eksamen_db;
USE eksamen_db;
SHOW TABLES;
SELECT * FROM brukere;
INSERT INTO brukere (username, password) VALUES ('test', '1234');
SELECT user, host FROM mysql.user;
GRANT ALL PRIVILEGES ON eksamen_db.* TO 'abdi'@'%';
FLUSH PRIVILEGES;
EXIT;
Flask
python app.py               # starter Flask
Git
git add .
git commit -m "eksamen"
git push
git status
