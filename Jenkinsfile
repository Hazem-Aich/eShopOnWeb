pipeline {
  agent any
  stages {
    stage('Buid') {
      steps {
        sh 'dotnet buid eShopOnWeb.sln'
      }
    }

    stage('Tests') {
      parallel {
        stage('Tests') {
          steps {
            sh 'dotnet test tests/UnitTests'
          }
        }

        stage('Integration') {
          steps {
            sh 'dotnet test tests/IntegrationTests'
          }
        }

        stage('Functional') {
          steps {
            sh 'dotnet test tests/FunctionalTests'
          }
        }

      }
    }

    stage('Deployment') {
      steps {
        sh 'dotnet publish eShopOnWeb.sln -o /var/aspnet'
      }
    }

  }
}