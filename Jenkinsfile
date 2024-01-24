pipeline {
    agent any 
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/Freddiefreeman/fooproject_fred.git'
            }
        }
        stage ('Build') {
            steps {
                bat "mvn compile"
            }
        }
        stage ('Test') {
            steps {
                bat "mvn test"
            }
            post {
                always {
                    junit '**/TEST*.xml'
				success {
					jacoco(execPattern: '**/build/jacoco/*.exec',
                    classPattern: '**/build/classes/java/main',
                    sourcePattern: '**/src/main')
				}
            }
        }
    }
}
