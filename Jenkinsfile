pipeline {
    agent any
    tools {
        maven "maven-3.8.4"
    }
    stages {
        stage('Build') {
            steps {
                checkout scm 
                sh "mvn -Dmaven.test.failure.ignore=true -s settings.xml clean deploy"
                // To run Maven on a Windows agent, use
                // bat "mvn -Dmaven.test.failure.ignore=true -s settings.xml clean package"
                
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
