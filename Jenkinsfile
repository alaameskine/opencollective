pipeline {
    agent any

    tools {
        nodejs 'NodeJS'
        dockerTool 'Docker'
    } 

    stages{
        //Running a dependency check to detect vulnerabilities 
        /* stage('Dependency Check'){
            steps {
            sh 'npm audit --audit-level=critical'
            }
        }

        //Running a code quality analysis to detect issues
        stage('SonarQube Analysis') {
            steps {
                /*withSonarQubeEnv('sonarqube') {            
                    sh 'npm run sonar'
            } 
            echo 'Check localhost:9000 for analysis details' 
        }
    }
        //Unit tests
        stage('Unit & Integration test') {
            steps {
                sh 'npm test'
            }
        } 

        //Building the app, running "npm start" would open port 3000
         stage('Build'){
            steps {
                sh 'npm install'
            }
        }

        stage('Deploy to Dockerhub'){
            steps {
                echo 'Running deploy_opencollective pipeline to do the deployment, it will start right after this build'
            }
    } */
    stage('Deploy to Dockerhub') {
        steps {
            docker.withRegistry('registry.hub.docker.com', 'dockerhub') {
                def customImage = docker.build("alaameskine/opencollective") 
                
                customImage.push()
                }
            }
        }
    }
}
