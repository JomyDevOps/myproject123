pipeline{
    agent any

    stages{
        stage("Git Checkout"){
            steps{
                git url: 'https://github.com/JomyDevOps/SpringBootFirstApp.git',branch: ${BRANCH_NAME}
            }
        }
    stage("Build"){
            steps{
                echo "Build Steps"
            }
        }
    stage("Test"){
            steps{
                echo "Test Steps"
            }
        }
    stage("Analysis"){
            steps{
                parallel(
                    "code analysis":{
                        echo 'SonarQube Scan'
                    },
                    "Security Scan":{
                        echo 'Checkmarx Scan'
                    }
                )
            }
        }
    stage("CD - Dev"){
            steps{
                echo "Dev Deploy Steps"
            }
        }
    stage("CD - QA"){
        when {
            anyOf{
                branch 'develop'
                branch 'release-*'
                branch 'release/*'
                branch 'master'
            }
        }
            steps{
                echo "QA Deploy Steps"
            }
        }
    stage("CD - Stage"){
        when {
            anyOf{
                branch 'release-*'
                branch 'release/*'
                branch 'master'
            }
        }
            steps{
                echo "Stage Deploy Steps"
            }
        }
    stage("CD - Prod"){
        when {
            anyOf{
                branch 'release-*'
                branch 'release/*'
                branch 'master'
            }
        }
            steps{
                echo "Prod Deploy Steps"
            }
        }
    }
}
