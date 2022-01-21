pipeline {
    agent any
    tools {
        maven "maven-3.8.4"
    }
    stages {
        stage('Build') {
            steps {
                git branch: 'main', url: 'https://github.com/sog4-devops/api-app.git'
                sh "mvn -Dmaven.test.failure.ignore=true clean install"
                // To run Maven on a Windows agent, use
                // bat "mvn -Dmaven.test.failure.ignore=true clean package"
            }
            post {
                success {
                    junit '**/target/surefire-reports/TEST-*.xml'
                    archiveArtifacts 'target/*.jar'
                }
            }
        }
         stage('deploy') {
            steps {
             echo "deployment started"
            }
         }
    }
}
