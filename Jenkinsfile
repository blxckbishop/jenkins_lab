pipeline {
    agent any

    stages {
 

        stage('Поиск файла prod.go') {
            steps {
                script {
                    def fileExists = fileExists('prod.go')
                    if (fileExists) {
                        echo 'Файл prod.go найден'
                    } else {
                        error('Файл prod.go не найден. Убедитесь, что файл присутствует локально.')
                    }
                }
            }
        }

        stage('Развертывание') {
            steps {
                script {
                    if (fileExists('prod.go')) {
                        echo 'Запуск скрипта развертывания deploy.sh'
			sh 'chmod +x deploy.sh'
                        sh './deploy.sh'
                    } else {
                        echo 'Файл prod.go не найден. Ничего не будет развернуто.'
                    }
                }
            }
        }
    }
}