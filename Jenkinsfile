pipeline {
    agent {
        node {
            label 'AGENT-1'
        }
    }
    environment { 
        GREETING = 'Hi Hello'
    }
     options {
        timeout(time: 1, unit: 'HOURS') 
        disableConcurrentBuilds()
    }
    parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')

        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')

        booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')

        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')

        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
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
                    echo 'Executing from shell script!'
                    echo "${GREETING}"
                    #sleep 10
                """
            }
        }
         stage('check params') {
            steps {
               sh """
                    echo "Hello ${params.PERSON}"

                    echo "Biography: ${params.BIOGRAPHY}"

                    echo "Toggle: ${params.TOGGLE}"

                    echo "Choice: ${params.CHOICE}"

                    echo "Password: ${params.PASSWORD}"
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
        aborted { 
            echo 'This runs when pipeline Timeout has been exceeded!'
        }
    }
}