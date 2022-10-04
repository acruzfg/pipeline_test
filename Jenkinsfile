pipeline {
    agent any
    environment{
        NEW_VERSION = '1.3.0'
        SERVER_CREDENTIALS = credentials('f6d57fbc-fc9c-4bf6-837c-e951cb67b687')
    }
    parameters {
        string(name: 'VERSION', defaultValue: '', description: 'version to deploy')
        booleanParam(name: 'executeTests', defaultValue: true, description: '')
    }
    stages {
        stage('Build') {
            steps {
                echo 'Building'
                echo "building version ${NEW_VERSION}"
            }
        }
        stage('Test') {
            when {
                expression{
                    params.executeTests
                }
            }
            steps {
                echo 'Testing' 
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying'
            }
        }
    }
}
