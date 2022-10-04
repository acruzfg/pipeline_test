def gv
pipeline {
    agent any 
    parameters {
        choice(name: 'HogwartsHouse', choices: ['Gryffindor', 'Hufflepuff', 'Ravenclaw', 'Slytherin'], description: 'Which Hogwarts House do you belong?')
        string(name: 'VERSION', defaultValue: '', description: 'version to deploy')
        booleanParam(name: 'executeTests', defaultValue: true, description: '')
        choice(name: 'HColor', choices: ['Red', 'Blue', 'Green', 'Yellow'], description: 'Select the color of you house')
        string(name: 'Alumni', defaultValue: 'Ale', description: 'you')
    }
    environment {
        SERVER_CREDENTIALS = credentials('f6d57fbc-fc9c-4bf6-837c-e951cb67b687')
    }

    stages {   
        stage ("Building") {
            steps {
                script {
                    gv=load "script.groovy"
                }
                withCredentials([
                    usernamePassword(credentialsId: 'f6d57fbc-fc9c-4bf6-837c-e951cb67b687', usernameVariable: 'USER', passwordVariable: 'PWD')]) {
                    echo " ${USER} and ${PWd}"}
            }

        }
        stage("Checking Ale's House") {
                when {
            expression {
                params.Alumni == 'Ale'
            }
        }
            steps {
                script{
                    gv.RED()
                }
            }
        }
        stage ("Checking your house") {
            steps {
                script{
                    echo "You're in ${HogwartsHouse}"
                }
            }
        }
    }
    post {
        always {
            script {
                if (params.Alumni == 'Ale') {
                    gv.RED()
                }
            }
        }
    }
}
