// ~/devops-study/Jenkinsfile
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/h00d-num/test-git-20260323.git'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Deploy') {
            steps {
                // 아까 설치한 'Deploy to container' 기능을 파이프라인용 스크립트로 쓴 거예요
                deploy artifacts: 'target/*.war', 
                       contextPath: '/myapp', 
                       war: '**/*.war',
                       containerAdapter: tomcat9(
                           url: 'http://192.168.56.102:8080',
                           credentialsId: 'tomcat-auth'
                       )
            }
        }
    }
}
