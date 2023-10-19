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
        sh "git clone https://github.com/chernihou/devopsangular.git"
      }
    }
    stage ("Generate backend image"){
      steps{
        dir("tp4Devops/springboot/app"){
          sh "mvn clean install"
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
        dir("devopsangular"){
        sh "docker compose up -d"
      }}}}}
