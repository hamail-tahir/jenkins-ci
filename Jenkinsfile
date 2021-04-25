pipeline {

    options {
        buildDiscarder(logRotator(numToKeepStr: '5', artifactNumToKeepStr: '5'))
    }

    parameters {
        booleanParam(name: 'WITH_DEPLOYMENT', defaultValue: false, description: 'Should I deploy?')
        choice(name: 'DEPLOYMENT_TARGET', choices: ['staging', 'integration', 'production'], description: 'Deployment target')
        choice(name: 'IMAGE_TYPE', choices: ['optimized', 'debug'], description: 'Image type to build')
    }

    agent {
        label "docker"
    }

    stages {
        stage('Set Up Stage') {
            steps {
         
            }
        }

        stage('Setup Project') {
            steps {
                
            }
        }

        stage('Static-Code Analysis') {
            steps {
                            }
        }

        stage('Unit- / Integration-Tests') {
            steps {
                
            }
        }

        stage('Contract-Tests') {
            steps {
              
            }
        }

        stage('Stash Build Sources') {
            steps {
            }
        }

        stage('Push to Sonarqube') {
            agent { label "master" }
            when {
                anyOf {
                    branch 'master'
                    branch 'release/*'
                    environment name: 'WITH_DEPLOYMENT', value: 'true'
                }
            }
            steps {
                unstash 'buildSources'
               
            }
        }

        stage('Make Container') {
            when {
                anyOf {
                    branch 'master'
                    branch 'release/*'
                    environment name: 'WITH_DEPLOYMENT', value: 'true'
                }
            }
            steps {
               
            }
        }

        stage('Deploy') {
            agent { label "master" }
            when {
                anyOf {
                    branch 'master'
                    environment name: 'WITH_DEPLOYMENT', value: 'true'
                }
            }
            steps {
                script {
                   
                }
                script {
                    
                }
            }
        }

    }

    post {
        always {
            sh ""
        }
      
    }
}
