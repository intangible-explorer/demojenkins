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
            }
        }
        stage('Environment Variables') {
            environment {
                username = 'nagesh'
            }
            steps {
                sh 'echo ${name}'
                sh 'echo ${username}'
            }
        }
        stage('Parameters') {
            steps {
                echo 'Deploy on Test'
                sh 'echo ${Person}'
                sh 'echo ${isMale}'
                sh 'echo ${City}'
            }
        }
        stage('Continue?') {
            input {
                message "Should we continue?"
                ok "Yes we should"
                
            }
            steps {
                echo 'Manual intervension success!'
            }
        }
        stage('Deploy on Prod') {
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
        }
        success {
            echo "Success!"
        }
    }
    
}
