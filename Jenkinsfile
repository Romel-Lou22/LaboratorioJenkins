pipeline {
  agent any

  stages {
    stage('Checkout') {
      steps {
        git url: 'https://github.com/Romel-Lou22/LaboratorioJenkins.git', branch: 'main'
      }
    }

    stage('Restore') {
      steps {
        // restaura la solución que está en la raíz
        sh 'dotnet restore *.sln'
      }
    }

    stage('Build') {
      steps {
        // compila la misma solución
        sh 'dotnet build *.sln --configuration Release'
      }
    }

    stage('Run') {
      steps {
        // cambia al directorio de tu proyecto y ejecuta sin recompilar
        dir('LaboratorioJenkins') {
          sh 'dotnet run --configuration Release --no-build'
        }
      }
    }
  }

  post {
    success { echo '✅ Pipeline completado' }
    failure { echo '❌ Falló el pipeline' }
  }
}
