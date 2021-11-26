pipeline {

    agent any

    parameters {
        choice(name: "Param1", choices: ["test1", "test2", "test3"], description: 'Just a testing parameter')
        booleanParam(name:"executeTests", defaultValue: true, description: '')
    }

    environment{
        NEW_VERSION = "1.3.0"
        SERVER_CREDENTIALS = credentials('global_git')
    }

    stages{

        stage("build"){

            steps{
                echo "building the application..."
                echo "version ${NEW_VERSION}"
                echo " deploying with ${SERVER_CREDENTIALS}"
                echo "testing param ${Param1}"
            }
                
        }

        stage("test"){
            when {
                expression {
                    BRANCH_NAME == "dev" && params.executeTests
                }
            }

            steps{
                echo "testing the application..."
            }

        }

        stage("deploy"){
                
            steps{
                echo "deploying the application..." 
            }
            
        }
    }
}