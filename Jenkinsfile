pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps { git url: 'https://github.com/Romel-Lou22/LaboratorioJenkins.git', branch: 'main' }
    }
    stage('Restore') {
      steps { sh 'dotnet restore LaboratorioJenkins/LaboratorioJenkins.sln' }
    }
    stage('Build') {
      steps { sh 'dotnet build LaboratorioJenkins/LaboratorioJenkins.sln --configuration Release' }
    }
    stage('Run') {
      steps {
        sh '''
          cd LaboratorioJenkins
          dotnet run --configuration Release --no-build
        '''
      }
    }
  }
  post {
    success { echo '✅ Pipeline completado' }
    failure { echo '❌ Falló el pipeline' }
  }
}
