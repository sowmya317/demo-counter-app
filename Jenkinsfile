pipeline {
    agent any
    tools { 
        maven'mvn'
    }
    stages{
        stage( 'git Checkout'){
            steps{
                git branch: 'main', credentialsId: 'gitrepo', url: 'https://github.com/sowmya317/demo-counter-app.git'
            }
        }
         stage( 'unit test'){
            steps{
                sh 'mvn test'

            }
        }
        stage( 'integration test'){
            steps{
                sh 'mvn verify -DskipUnitTests'

            }
            
        }
         stage( 'static code analysis'){
            steps{
                sh 'mvn clean package '

            }
        }     
        stage( 'upload war files to nexus'){
            steps{
                script{
           
                    nexusArtifactUploader artifacts: [[artifactId: 'springboot', classifier: '', file: 'target/Uber.jar', type: 'jar']], credentialsId: 'nexus', groupId: 'com.example', nexusUrl: '3.93.73.154:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'webapp', version: '1.0.0'
                }
                

            }
    }
} 
}
