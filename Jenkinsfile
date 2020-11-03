pipeline {

    agent {
        docker {
            image 'maven:3.6.3-jdk-11'
        }
    }

    stages {
        stage('Clone') {
            steps {
                checkout scm
            }
        }

        stage('build') {
            steps {
                sh "mvn -B -s /usr/share/maven/ref/settings-docker.xml package"
            }
        }
    }

    post {
        always {
            junit "**/surefire-reports/**/*.xml"
        }
    }
}