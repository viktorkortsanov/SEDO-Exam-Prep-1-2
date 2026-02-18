pipeline {
    agent any
    stages {
        stage("Install .NET 6.0") {
            steps {
                bat "choco install dotnet-6.0-sdk -y"
            }
        }
        stage("Restore dependencies") {
            when {
                anyOf {
                    branch 'main'
                    branch 'feature'
                }
            }
            steps {
                bat "dotnet restore"
            }
        }
        stage("Build the application") {
            when {
                anyOf {
                    branch 'main'
                    branch 'feature'
                }
            }
            steps {
                bat "dotnet build --no-restore"
            }
        }
        stage("Test the application") {
            when {
                anyOf {
                    branch 'main'
                    branch 'feature'
                }
            }
            steps {
                bat "dotnet test --no-build --verbosity normal"
            }
        }
    }
}
