pipeline {
    agent any
    enviroment{
        NEW_VERSION = '1.3.0'
        SERVER_CREDENTIALS = credentials('f6d57fbc-fc9c-4bf6-837c-e951cb67b687')
    }
    stages {
        stage('Build') {
            steps {
                echo 'Building'
                echo "building version ${NEW_VERSION}"
            }
        }
        stage('Test') {
            steps {
                echo 'Testing' 
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying'
                withCredentials([
                    usernamePassword(credentials: 'f6d57fbc-fc9c-4bf6-837c-e951cb67b687', usernameVariable: USER, passwordVariable: PWD)
                ]){
                    sh "some script ${USER} ${PWD}"
                }
            }
        }
    }
}
