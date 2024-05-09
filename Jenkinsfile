pipeline {
    agent any
    stages{
        stage(build){
            steps{
                echo "Bulding.."
            }
            post{
                always{
                    mail to:s223645405@deakin.edu.au
                    subject:"build status mail"
                    body: "build log attached"
                }
            }
    }
    stage("test"){
        steps{
            echo "Testing.."
        }
    }
    stage("deploy"){
        steps{
            echo "Deploying"
        }
    }
    }
}
