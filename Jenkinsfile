pipeline {
    agent any
    tools {
        maven 'Maven'
    }
    stages {
        stage("Test") {
            steps {
                sh 'mvn test'
            }
        }
        stage("Build") {
            steps {
                sh 'mvn package'
            }
        }
        
        stage("Deploy on Tomcat") {
            input {
                message "Should we continue?"
                ok "Yes, we should."
                }
            }
            steps {
                deploy adapters: [tomcat9(credentialsId: 'credentialForTomcatAdmin', path: '', url: 'http://192.168.23.131:8081')], contextPath: '/myapp', war: '**/*.war'
            }
        }    
    }

}