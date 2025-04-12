colocar apontar para o ip no front-end
mask no ip para apresentar um dominio // usar ngnix
alterar stores no front para o ip certo ou dominio masked

192.168.80.1  --> ip do server
user : rvieira 
pass : admin123

apagar lixo: 
docker system prune -a
sudo docker container prune  && \
sudo docker network prune  && \
sudo docker image prune  && \
sudo docker system prune -a  --volumes

verificar espaço do disco
sudo docker system df

meter containers up
sudo docker-compose up /down