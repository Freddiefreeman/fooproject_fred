pipeline {
    agent any 

    environment {
        def myString = "Hello, User."
        def myNumber = 5
        def myBool = true
    }

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
					jacoco(
                    execPattern: '**/build/jacoco/*.exec',
                    classPattern: '**/build/classes/java/main',
                    sourcePattern: '**/src/main'
                    exclusionPattern: 'src/test*'
                    )
                }
            }
        }
    }
}
