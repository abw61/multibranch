stage('build') {
   node{
      git 'https://github.com/beedemo/mobile-deposit-api.git'
      writeFile encoding: 'UTF-8', file: 'config', text: 'version=1'
      stash includes: 'pom.xml,config', name: 'pom-config'
      //def mvnHome = tool 'M3'
      //sh "${mvnHome}/bin/mvn -B verify"
      docker.image('maven:3.3.3-jdk-8').inside() {
        sh 'mvn -B verify'
      }

   }
}


stage('test'){
   node {
      unstash 'pom-config'
      configValue = readFile encoding: 'UTF-8', file: 'config'
      echo configValue
   }
}



stage('deploy') {
  input message: 'Do you want to deploy?'
  node {
    echo 'deployed'
  }
}
