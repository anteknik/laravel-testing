### Laravel Ruthless Testing*

Berasa kenal dengan pemilik tulisan diblog ini http://agilist.rizkysyaiful.com/testing-di-laravel-bag-1/ dan meminjam judul istilah dari om endy http://software.endy.muhardin.com/java/ruthless-testing-1/  
saya coba tuliskan kelanjutannya mengambil dari artikel https://phpkoder.wordpress.com/2012/07/26/mengintegraikan-projek-php-dengan-jenkins-part-1/
saya juga akan mencoba beberapa Auto Testing Framework Untuk PHP http://liputanwebsite.com/ini-dia-10-auto-testing-framework-untuk-php-yang-bisa-dicoba/.
Menggunakan Git sebagai control version kenapa? https://ridwanbejo.wordpress.com/2015/02/16/kenapa-saya-menggunakan-layanan-git/
Menggunakan vagrant kenapa? berikut penjelasannya bisa dilihat http://id.phptherightway.com/#vagrant dan menurut documentasinya dari laravel sangat direkomendasikan
menggunakan homestead berikut cara instalasinya http://ambercat.rahmanda.net/collections/2015/02/18/instalasi-homestead.html

# Menginstall Jenkins PHP Continous Integration di laravel/homestead

# PHP Quality Assurance Tools
composer global require "phpunit/phpunit=4.1.*"
composer global require behat/behat='~3.0.6'
composer global require 'phploc/phploc=*'
composer global require 'phpmd/phpmd=*'
composer global require 'squizlabs/php_codesniffer=*'
composer global require 'sebastian/phpcpd=*'
composer global require 'sebastian/phpdcd=*'

# Update 
sudo apt-get update

# Install php5-xsl
sudo apt-get install php5-xsl

# Install Jenkins
wget -q -O - https://jenkins-ci.org/debian/jenkins-ci.org.key | sudo apt-key add -
sudo sh -c 'echo deb http://pkg.jenkins-ci.org/debian binary/ > /etc/apt/sources.list.d/jenkins.list'
sudo apt-get update
sudo apt-get install jenkins

# set 8080 port for nginx
sudo sed '/listen 80;/a listen 8080;' /etc/nginx/sites-available/homestead.app
sudo service nginx restart

#get the php job template
curl -L https://raw.githubusercontent.com/sebastianbergmann/php-jenkins-template/master/config.xml | \
 java -jar jenkins-cli.jar -s http://localhost:8080 create-job php-jenkins

#Halaman Jenkins
#clone github repository testinglaravel di https://github.com/anteknik/laravel-testing.git 
 struktur folder file dan build copy ke folder project laravel
#Konfigurasi Git Jenkins plugin

#Build History



