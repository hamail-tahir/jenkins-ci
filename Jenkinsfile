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
        label "any"
    }

    stages {
        stage('Set Up Stage') {
            steps {
                echo "Stage 1"
            }
        }

        stage('Setup Project') {
            steps {
                echo "Stage 2"
            }
        }

        stage('Static-Code Analysis') {
            steps {
                echo "Stage 3"
                            }
        }

        stage('Unit- / Integration-Tests') {
            steps {
                echo "Stage 4"
            }
        }

        stage('Contract-Tests') {
            steps {
              echo "Stage 5"
            }
        }

        stage('Stash Build Sources') {
            steps {
                echo "Stage 6"
            }
        }

        stage('Push to Sonarqube') {
            // agent { label "master" }
            when {
                anyOf {
                    branch 'master'
                    branch 'release/*'
                    environment name: 'WITH_DEPLOYMENT', value: 'true'
                }
            }
            steps {
               echo "push to SC"
               
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
               echo "Container making"
            }
        }

        stage('Deploy') {
            // agent { label "master" }
            when {
                anyOf {
                    branch 'master'
                    environment name: 'WITH_DEPLOYMENT', value: 'true'
                }
            }
            steps {
                script {
                   echo "Deployed"
                }
      
            }
        }

    }

    post {
        always {
            sh "end"
        }
      
    }
}
