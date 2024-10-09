<h1>Created 2-tier Architecture in AWS</h1>
<h3>Step 1: Launch one Instance for Frontend</h3>

![image](https://github.com/user-attachments/assets/bcc3bad3-6e4e-48f6-b8bf-0715ebcb25f6)

<h3>Step 2: Launch another Instance for Backend and PostgreSQL</h3>

![image](https://github.com/user-attachments/assets/787efc35-0bab-458d-9d21-e07119413274)

<h3>Step 3: Connect Frontend Instance </h3>
sudo apt update<br>
sudo apt install -y nodejs npm<br>
sudo npm install -g n<br>
sudo n 14.17.0 node -v0<br>
sudo apt-get install git-all -y<br>
git clone https://github.com/shubhamkalsait/devops-fullstack-app.git<br>
cd devops-fullstack-app/frontend/<br>
sudo vim .env 	REACT_APP_SERVER_URL=http://backend_pub_ip:8080/employees<br>
npm install<br>
npm start<br>
<h3>Step 4: Connect Backend and PostgreSQL Instance</h3>
sudo apt update<br>
sudo apt install postgresql postgresql-contrib -y<br>
sudo passwd postgres<br>
sudo -u postgres psql<br>
CREATE DATABASE db_name; #employees<br>
CREATE USER user_name WITH PASSWORD 'password'; #test #'1234'<br>
GRANT ALL PRIVILEGES ON DATABASE db_name TO user_name; #employees #test<br>
\c your_db_name<br>
GRANT USAGE ON SCHEMA public TO your_user;<br>
GRANT ALL PRIVILEGES ON SCHEMA public TO your_user;<br>
GRANT ALL PRIVILEGES ON ALL TABLES IN SCHEMA public TO your_user;<br>
ALTER DEFAULT PRIVILEGES IN SCHEMA public GRANT ALL ON TABLES TO your_user;<br>
\q<br>
exit<br>
sudo curl -O https://dl.google.com/go/go1.19.linux-amd64.tar.gz<br>
sudo tar -xvf go1.19.linux-amd64.tar.gz<br>
sudo mv go /usr/local<br>
export GOROOT=/usr/local/go<br>
export GOPATH=$HOME/go<br>
export PATH=$GOPATH/bin:$GOROOT/bin:$PATH<br>
sudo snap install go --classic<br>
sudo apt-get install git-all -y<br>
git clone https://github.com/shubhamkalsait/devops-fullstack-app.git<br>
cd devops-fullstack-app/backend/<br>
sudo DB_HOST=localhost DB_USER=<your_username> DB_PASSWORD=<your_password> DB_NAME=<your_dbname> DB_PORT=5432 ALLOWED_ORIGINS="http://frontend_pub_ip:3000" go run main.go<br>
<br>
  
**Must have 5432,8080 & 3000 port in Security Group** <br>

<h3>Step 5: Paste the IP of Frontend Instance </h3>

![image](https://github.com/user-attachments/assets/b1168d0e-d6de-4fdd-9ead-954d1571ad2d)

**Successfully Hosted the application react language as a frontend, go language as a backend and postgresql as a database**     

