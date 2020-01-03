pipeline {
  agent {
    docker {
      image 'ubuntu:bionic'
      args '-u root:root'
    }

  }
  stages {
    stage('Build') {
      steps {
        sh '''apt update
apt install -y apache2 curl net-tools
cp ./index.html /var/www/html/
/etc/init.d/apache2 start'''
      }
    }

    stage('pre-check') {
      steps {
        sh '''netstat -taupen
cat /var/www/html/index.html'''
      }
    }

    stage('Test') {
      steps {
        sh 'curl 127.0.0.1'
      }
    }

  }
}