pipeline {
    agent any
	stages {
		stage('Checkout and Run First Script') {
			steps {
				script {
					// Запускаем скрипты
					echo 'Running test1.sh in a separate shell'
					sh 'chmod +x test1.sh' // Убедитесь, что скрипт имеет права на выполнение
					sh 'nohup ./test1.sh &' // Запускаем в отдельном процессе
				}
			}
		}
			
		stage('Checkout and Run Second Script') {
	            steps {
	                script {
	                	echo 'Running test2.sh in steps'
	                	sh 'chmod +x test2.sh' // Убедитесь, что скрипт имеет права на выполнение
	                	sh './test2.sh' // Запускаем в текущем процессе	
				}
			}
		}
			
		stage('Checkout and Run Third Script') {
	            steps {
	                script {
	                	echo 'Running test3.sh'
	                	sh 'chmod +x test3.sh' // Убедитесь, что скрипт имеет права на выполнение
	                	sh './test3.sh' // Запускаем в текущем процессе	
	            		}
			}
		}
	}	
}
