
pipeline {
    agent { label 'maven-label' }

    tools {
    
        maven "M3"
    }

    stages {
        stage('Build') {
            steps {
                
                git branch: 'main', url: 'https://github.com/slesha-app/my-app.git'

                // Run Maven on a Unix agent.
                sh "mvn -Dmaven.test.failure.ignore=true -s settings.xml clean deploy"

                // To run Maven on a Windows agent, use
                // bat "mvn -Dmaven.test.failure.ignore=true -s settings.xml clean deploy"
            }

            post {
                success {
                    junit '**/target/surefire-reports/TEST-*.xml'
                    archiveArtifacts 'target/*.jar'
                }
            }
        }
    }
}
