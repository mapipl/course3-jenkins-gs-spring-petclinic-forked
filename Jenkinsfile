pipeline {
    agent any
    
    stages {
        stage("build") {
            steps {
                sh "./mvnw package"
            }
        }
        
        stage("capture") {
            steps {
                archiveArtifacts artifacts: '**/target/*.jar'
                jacoco()
                junit '**/target/surefire-reports/TEST*.xml'
            }
        }
    }
    
    post {
        always {
            sh "echo send mail"
        }
    }
}