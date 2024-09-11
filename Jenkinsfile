pipeline {
    agent any
    
    tools {
        maven 'maven'
    }
    
    stages {
        stage("Git Checkout") {
            steps {
                git branch: 'main', url: 'https://github.com/Nandini-1428/test-petclinic-app.git'
            }
        }
        stage("Compile") {
            steps {
                sh "mvn compile"
            }
        }
        stage("Test") {
            steps {
                sh "mvn test -DskipTests=true"
            }
        }
        stage("Build") {
            steps {
                sh "mvn package -DskipTests=true"
            }
        }
        stage('Deploy') {
            steps {
                deploy adapters: [tomcat9(url: 'http://52.66.212.104/:8080',
                            credentialsId: 'tomcat-server')],
                        war: 'target/*.war',
                        contextPath: 'app1'
            }
        }
    }
}
