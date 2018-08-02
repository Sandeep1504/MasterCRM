pipeline {
    agent any
    stages {
        
        stage ('Checkout SCM'){
            
            steps{
            
            checkout([$class: 'GitSCM', branches: [[name: '*/master'], [name: '*/master/BranchOne']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: '653394bb-0f75-4911-9759-9712c4eabf4c', url: 'https://github.com/Sandeep1504/A-Automate-Test.git']]])
          
            }
        }
        
        
        stage ('Build Stage') {

            steps {
                withMaven(maven : 'MAVEN_HOME') {
                    sh 'mvn clean install -U'
                

                    sh 'mvn compile'
                    sh 'echo "Building...."'
                    
                }
            }
        }

        stage ('Testing Stage') {

            steps {
                withMaven(maven : 'MAVEN_HOME') {
                    sh 'mvn test -P single'
                }
            }
        }


        stage ('Deployment Stage') {
            steps {
                sh 'echo "Deloying...."'
                }
            }
        }
    }
