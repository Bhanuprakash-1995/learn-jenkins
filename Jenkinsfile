pipeline {
    agent {
        node {
            label 'AGENT-1'
        }
    }
    environment { 
        GREETING = 'Hi Hello'
    }
    // build
    stages {
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                sh """
                    echo 'Deploying....'
                    echo "${GREETING}"
                """
            }
        }
    }
    // post build
    post { 
        always { 
            echo 'I will always get executed irrespective of the pipeline status!'
        }
        failure { 
            echo 'This runs when pipeline is failed, used to send some alerts using slack..etc'
        }
        success { 
            echo 'This runs when pipeline executed successfully!'
        }
    }
}