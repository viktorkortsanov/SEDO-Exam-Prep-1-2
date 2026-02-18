pipeline{
    agent any
    stages{
        stage("Restore dependencies"){
            when {
                anyof {
                    branch 'main'
                    branch 'feature'
                }
            }
            steps{
                bat "dotnet restore"
            }
        }
        stage("Build the application"){
            when {
                anyof {
                    branch 'main'
                    branch 'feature'
                }
            }
            steps{
                bat "dotnet build --no-restore"
            }
        }
        stage("Test the application"){
            when {
                anyof {
                    branch 'main'
                    branch 'feature'
                }
            }
            steps{
                echo "dotnet test --no-build --verbosity normal"
            }
        }
    }
}