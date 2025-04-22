Como Criar o Script


Primeiro você cria um arquivo com o comando nano e nomeia como script.sh, depois adiciona os comandos abaixo dentro do script :
#! /bin/bash

if [ -x /etc/init.d/apache2 ]; then

echo “apache não encontrado, iniciando a instalação….”

sudo apt-get update

sudo apt-get install apache2 -y

else

echo “você ja possui um apache instalado”

fi

sudo mkdir -p /var/www/ifrn/public_html

cd /var/www/ifrn/public_html

sudo git clone
https://github.com/matheusmanuel/site-simples-com-html-e-css-.git sudo
cp -r site-simples-com-html-e-css-/* . sudo rm -rf
site-simples-com-html-e-css-/ cd /etc/apache2/site-available/

sudo tee ifrn.conf<<EOF

<VirtualHost *:80>

ServerAdmin admin@ifrn

ServerName ifrn

ServerAlias www.ifrn

DocumentRoot /var/www/ifrn/public_html ErroLog ${APACHE_LOG_DIR}/error.log

CustomLog ${APACHE_LOG_DIR}/access.log combined

</VirtualHost>

EOF

sudo a2ensite ifrn.conf

sudo echo “127.0.0.1 tfrn” | sudo tee -a /etc/hosts

sudo /etc/init.d/apache2 restart

sudo /etc/init.d/apache2 status

Após isso você vai na pasta do apache em /etc/apache2/sites-avaliable 
da um LS e pega o arquivo site1.conf e copia tudo que tem dentro no arquivo
Depois você da um comando cat site1.conf e vai para a pasta /home/usuário e abre o script
apaga a parte <virtualhost e cola os dados que você copiou do arquivo site1
após isso coloca o comando sudo a2ensite aluno.conf e abaixo o comando sudo echo "127.0.0.1 aluno " | sudo tee -a /etc/hosts
agora o comando para reiniciar o apache " sudo /etc/init.d/apache2 restart e salva o script
note que ele vai estar sem permissão de execução
use o comando sudo chmod +x script para habilitar
e depois só executar o script com o comando " ./script.sh " 
após isso só ir ao navegador e verificar se o site ficou no ar.





