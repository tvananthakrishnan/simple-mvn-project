pipeline {
    agent any
    stages {
        stage('Build Application') {
            steps {
                sh 'mvn -f simple-maven-app/pom.xml clean package'
            }
            post {
                success {
                    echo "Now Archiving the Artifacts...."
                    archiveArtifacts artifacts: '**/*.war'
                }
            }
        }
        stage('Deploy in Staging Environment'){
            steps{
                build job: 'Tomcat_Deployment'

            }
            
        }
        stage('Deploy to Production'){
            steps{
                timeout(time:5, unit:'DAYS'){
                    input message:'Approve PRODUCTION Deployment?'
                }
                build job: 'Tomcat_Deployment_prod'
            }
        }
    }
}
