pipeline {
    agent any
    stages {
        stage("Setup .NET") {
            steps {
                bat "choco install dotnet-6.0-sdk --version=6.0.4 -y || choco upgrade dotnet-6.0-sdk -y"
                bat "dotnet --version"
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