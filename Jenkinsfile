jsl = library(
  identifier: "shared-library@master",
  retriever: modernSCM(
    [
      $class: 'GitSCMSource',
      remote: 'https://github.com/RaunakRoy96/jenkins-library.git'
    ]
  )
)

imageNameWithUserid = 'raunakroy/springboot'
credentials = '47f84f4d-ab54-4743-8250-875b54c8bab9'
port1 = '8003'
port2 = '8080'

node('master') {
    stage('pull') {
        scmCheckout(this)
    }
    stage('sonar') {
        sonarAnalysis this, 'JDK 8', 'MAVEN_HOME'
    }
   stage('build') {
       buildWithMaven(this,  'JDK 8', 'MAVEN_HOME')
    //   withMaven (
    //     maven: 'MAVEN_HOME',
    //     jdk: 'JDK 8') {
    //     sh 'mvn clean install';
    //     } 
   }
   stage('docker') {
       //sh 'docker-compose up -d'
    //   docker.withRegistry('https://registry-1.docker.io/v2/', '47f84f4d-ab54-4743-8250-875b54c8bab9') {
    //         docker.build('raunakroy/springboot').push()
    //   }
    dockerBuildAndPush(this, this.imageNameWithUserid, this.credentials)
   }
   
   stage('docker deploy') {
       dockerPullAndRun(this, this.imageNameWithUserid, this.credentials, this.port1, this.port2)
   }
}
   
