pipeline {
  agent any
  tools {nodejs "NodeJS"}
    stages {
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }
        stage('Test') {
                    steps {
                        sh "chmod +x -R ${env.WORKSPACE}"
                        sh './jenkins/test.sh'
                    }
                }
                stage('Deliver') {
                            steps {
                                sh "chmod +x -R ${env.WORKSPACE}"
                                sh './jenkins/deliver.sh'
                                input message: 'Finished using the web site? (Click "Proceed" to continue)'
                                sh "chmod +x -R ${env.WORKSPACE}"
                                sh './jenkins/kill.sh'
                                }
                            }
    }
}