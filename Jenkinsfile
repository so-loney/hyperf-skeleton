pipeline {
  agent {
    docker {
      image 'hyperf/hyperf:7.2-alpine-cli'
      args '-v /tmp/skeleton:/hyperf-skeleton -p 9501:9501 -it --entrypoint /bin/sh'
    }

  }
  stages {
    stage('build') {
      steps {
        sh '''wget https://github.com/composer/composer/releases/download/1.8.6/composer.phar

chmod u+x composer.phar

mv composer.phar /usr/local/bin/composer

composer config -g repo.packagist composer https://mirrors.aliyun.com/composer

composer create-project hyperf/hyperf-skeleton

cd hyperf-skeleton

php bin/hyperf.php start'''
      }
    }

  }
}