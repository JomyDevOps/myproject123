pipeline{
    agent any

    stages{
        stage("Git Checkout"){
            steps{
                url: 'https://github.com/JomyDevOps/SpringBootFirstApp.git'
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
    stage("Deploy"){
            steps{
                echo "Deploy Steps"
            }
        }
    }
}
