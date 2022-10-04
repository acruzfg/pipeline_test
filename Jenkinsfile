pipeline {
    agent any
    environment{
        NEW_VERSION = '1.3.0'
        SERVER_CREDENTIALS = credentials('f6d57fbc-fc9c-4bf6-837c-e951cb67b687')
    }
    parameters {
        choice(name: 'Hogwarts house', choices: ['Gryffindor', 'Hufflepuff', 'Ravenclaw', 'Slytherin'], description: 'Which Hogwarts House do you belong?')
        string(name: 'VERSION', defaultValue: '', description: 'version to deploy')
        booleanParam(name: 'executeTests', defaultValue: true, description: '')
        choice(name: 'House color', choices: ['Red', 'Blue', 'Green', 'Yellow'], description: 'Select the color of you house')
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
