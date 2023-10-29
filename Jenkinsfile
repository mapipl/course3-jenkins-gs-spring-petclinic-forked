pipeline {
    agent any
    
    stages {
        stage("checkout") {
            steps {
                git branch:'main', url: 'https://github.com/mapipl/course3-jenkins-gs-spring-petclinic-forked.git'
            }
        }
        
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