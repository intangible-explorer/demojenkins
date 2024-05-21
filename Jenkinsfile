pipeline {
    agent any
    environment {
        name = 'shubham'
    }
    parameters {
        string(name: 'Person', defaultValue: 'Ayush Yadav', description: 'Who are you?')
        booleanParam(name: 'isMale', defaultValue: true, description: 'Is male ?')
        choice(name: 'City', choices: ['Pune', 'Mumbai', 'Banglore'], description: 'Preferred City ?')
    }
    stages {
        stage('Run A Command') {
            slackSend channel: 'jenkins-pipeline-notification-test', message: 'Run A Command Job Started'
            steps {
                sh '''
                    ls
                    date
                    pwd
                    cal 2024
                '''
            }
        }
        stage('Environment Variables') {
            slackSend channel: 'jenkins-pipeline-notification-test', message: 'Environment Variables Job Started'
            environment {
                username = 'nagesh'
            }
            steps {
                sh 'echo ${name}'
                sh 'echo ${username}'
            }
        }
        stage('Parameters') {
            slackSend channel: 'jenkins-pipeline-notification-test', message: 'Parameters Job Started'
            steps {
                echo 'Deploy on Test'
                sh 'echo ${Person}'
                sh 'echo ${isMale}'
                sh 'echo ${City}'
            }
        }
        stage('Continue?') {
            slackSend channel: 'jenkins-pipeline-notification-test', message: 'Continue Job Started'
            input {
                message "Should we continue?"
                ok "Yes we should"
                
            }
            steps {
                echo 'Manual intervension success!'
            }
        }
        stage('Deploy on Prod') {
            slackSend channel: 'jenkins-pipeline-notification-test', message: 'Deploy on Prod Job Started'
            steps {
                echo 'Deploy on Prod'
            }
        }
    }
    post {
        always {
            echo "This will always run !"
        }
        failure {
            echo "Failure!"
            slackSend channel: 'jenkins-pipeline-notification-test', message: 'Pipeline execution Failed!'
        }
        success {
            echo "Success!"
            slackSend channel: 'jenkins-pipeline-notification-test', message: 'Pipeline executed Successfully'
        }
    }
    
}
