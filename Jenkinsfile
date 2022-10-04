def gv
pipeline {
    agent any 
    parameters {
        choice(name: 'Hogwarts house', choices: ['Gryffindor', 'Hufflepuff', 'Ravenclaw', 'Slytherin'], description: 'Which Hogwarts House do you belong?')
        string(name: 'VERSION', defaultValue: '', description: 'version to deploy')
        booleanParam(name: 'executeTests', defaultValue: true, description: '')
        choice(name: 'House color', choices: ['Red', 'Blue', 'Green', 'Yellow'], description: 'Select the color of you house')
        string(name: 'Message', defaultValue: '', description: 'Include a brief cheer messaging for sending the gift:')
        string(name: 'SENDER', defaultValue: '', description: 'Include a brief cheer messaging for sending the gift:')
        choice(name: 'Color', choices: ['Red', 'Blue', 'Gold'], description: 'Select the color box for the gift')
        booleanParam(name: 'YES', defaultValue: false, description: 'Would you like to include a tres leches cake?')
    }
    environment {
        NEW_VERSION = '1.3.0'
        SERVER_CREDENTIALS = credentials('f6d57fbc-fc9c-4bf6-837c-e951cb67b687')
    }

    stages {
        
        stage ("Checking credentials your HG house") {
            steps {
                script {
                    gv=load "script.groovy"
                }
                withCredentials([
                    usernamePassword(credentialsId: 'test-cred', usernameVariable: 'PW1', passwordVariable: 'PW2')]) {
                    echo "My password is ${PW1} and ${PW2}!"
    
}
            }

        }
        stage("Building the present") {
                when {
            expression {
                params.SENDER == 'Hailey'
            }
        }
            steps {
                script{
                    gv.BuildGift()
                }

                echo "Grapping the gift in the ${Color} box "
            }
        }
        stage ("Testing the box toughness") {
            when {
            expression {
                params.SENDER == 'Hailey'
            }
        }
            steps {
                script{
                    gv.TestApp()
                    echo 'yeah, it seems like it can survive the trip'
                }
            }
        }
        stage ("Deploy gift") {
            when {
            expression {
                params.SENDER == 'Hailey'
            }
        }
            steps {
                script{
                    gv.DepApp()
                    echo "The videogame ${Game} has been deployed to Daniel with the following note:"
                    echo "Note: ${Message}"
                    if (params.YES) {
                    echo 'and tysm for the cake :)'

                    } else {
                    echo 'you could had added a cake, tho...'
                    }

                }

                
                
            }

        }
    }
    post {
        always {
            script {
                if (params.SENDER == 'Hailey') {
                    echo ':)'

                } else {
                    echo 'srry, only Hailey can send gifts...'
                }
            }
        }
    }
}
