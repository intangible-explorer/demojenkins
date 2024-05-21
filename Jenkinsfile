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
            steps {
                sh '''
                    ls
                    date
                    pwd
                    cal 2024
                '''
                slackSend channel: 'jenkins-pipeline-notification-test', message: 'Run A Command Job Started'
            }
        }
        stage('Environment Variables') {
            environment {
                username = 'nagesh'
            }
            steps {
                sh 'echo ${name}'
                sh 'echo ${username}'
                slackSend channel: 'jenkins-pipeline-notification-test', message: 'Environment Variables Job Started'
            }
        }
        stage('Parameters') {
            steps {
                echo 'Deploy on Test'
                sh 'echo ${Person}'
                sh 'echo ${isMale}'
                sh 'echo ${City}'
                slackSend channel: 'jenkins-pipeline-notification-test', message: 'Parameters Job Started'
            }
        }
        stage('Continue?') {
            input {
                message "Should we continue?"
                ok "Yes we should"
                
            }
            steps {
                echo 'Manual intervension success!'
                slackSend channel: 'jenkins-pipeline-notification-test', message: 'Continue Job Started'
            }
        }
        stage('Deploy on Prod') {
            steps {
                echo 'Deploy on Prod'
                slackSend channel: 'jenkins-pipeline-notification-test', message: 'Deploy on Prod Job Started'
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
