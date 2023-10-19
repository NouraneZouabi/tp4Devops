pipeline{
  agent any 
  tools {
    maven 'Maven'
    nodejs 'node'
  }
  stages {
    stage ("Clean up"){
      steps {
        deleteDir()
      }
    }
    stage ("Clone repo"){
      steps {
                git branch: 'main', url: 'https://github.com/NouraneZouabi/tp4Devops'
                sh "mvn -Dmaven.test.failure.ignore=true clean package"
      }
    }
    stage ("Generate backend image"){
      steps{
        dir("tp4Devops/springboot/app"){
          sh "maven clean install"
          sh "docker build -t devopsangular ."
        }
      }
    }
    stage ("Build Angular"){
  steps {
    dir("tp4Devops/angular-app"){ 
       
        sh "docker build -t angular ."  
    }
  }
}
    stage ("Run docker compose"){
      steps { 
        dir("tp4Devops"){
        sh "docker compose up -d"
      }}}}}
