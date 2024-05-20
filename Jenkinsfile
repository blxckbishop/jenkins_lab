pipeline {
    agent any

    triggers {
        cron('*/2 * * * *') // Запускать каждые две минуты
    }

    stages {
        stage('Checkout and Deploy') {
            steps {
                script {
                    // Проверяем репозиторий на наличие изменений
                    checkout([$class: 'GitSCM', branches: [[name: '*/prod']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/blxckbishop/jenkins_lab.git']]])

                    // Проверяем наличие файла prod.go
                    if (fileExists('prod.go')) {
                        // Запускаем скрипт deploy.sh
                        sh 'chmod +x deploy.sh' // Убедитесь, что скрипт имеет права на выполнение
                        sh './deploy.sh'
                    } else {
                        echo 'File prod.go not found. Skipping deployment.'
                    }
                }
            }
        }
    }
}