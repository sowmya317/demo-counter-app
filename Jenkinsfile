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
    }
}  
