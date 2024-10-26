pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                bat 'dotnet build eShopOnWeb.sln'
            }
        }

        stage('Tests') {
            parallel {
                stage('Unit Tests') {
                    steps {
                        bat 'dotnet test tests/UnitTests'
                    }
                }

                stage('Integration Tests') {
                    steps {
                        bat 'dotnet test tests/IntegrationTests'
                    }
                }

                stage('Functional Tests') {
                    steps {
                        bat 'dotnet test tests/FunctionalTests'
                    }
                }
            }
        }

        stage('Deployment') {
            steps {
                bat 'dotnet publish eShopOnWeb.sln -o C:\\var\\aspnet'
            }
        }
    }
}
