pipeline{
    agent {label 'sonar'}
    stages{
       stage('Git Checkout Stage'){
            steps{
                git branch: 'master', url: 'https://github.com/AmruthKalva/Sud-Calculator-java.git'
            }
         }        
       stage('Build Stage'){
            steps{
                sh 'mvn clean install'
            }
         }
        stage('SonarQube Analysis Stage') {
            steps{
                withSonarQubeEnv('sonar') { 
                    sh "mvn clean verify sonar:sonar -Dsonar.projectKey=calc"
                }
            }
        }
    }
}
