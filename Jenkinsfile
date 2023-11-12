node {
  stage('SCM') {
    checkout scm
  }
  stage('SonarQube Analysis') {
    def scannerHome = tool 'SonarScanner for MSBuild'
    withSonarQubeEnv(installationName: 'sonar', credentialsId: 'admin_sonar') {
      bat "dotnet ${scannerHome}\\SonarScanner.MSBuild.dll begin /k:\"girijaproj\""
      bat "dotnet build"
      bat "dotnet ${scannerHome}\\SonarScanner.MSBuild.dll end"
    }
  }
}


  
