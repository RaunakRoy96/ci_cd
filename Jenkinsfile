
jsl = library(
  identifier: "shared-library@master",
  retriever: modernSCM(
    [
      $class: 'GitSCMSource',
      remote: 'https://github.com/RaunakRoy96/jenkins-library.git'
    ]
  )
)

properties([
  parameters([
    string(name: 'imageNameWithUserid', defaultValue: 'raunakroy/springboot', description: '' ),
    string(name: 'credentials', defaultValue: '47f84f4d-ab54-4743-8250-875b54c8bab9', description: '' ),
    string(name: 'port1', defaultValue: '8003', description: '' ),
    string(name: 'port2', defaultValue: '8080', description: '' ),
    string(name: 'host', defaultValue: 'dev', description: '' )
   ])
])


node('master') {
  try {
      stage('pull') {
          scmCheckout(this)
      }
    
      stage('sonar') {
          sonarAnalysis this, 'JDK 8', 'MAVEN_HOME'
      }
    stage('build') {
        buildWithMaven(this,  'JDK 8', 'MAVEN_HOME')
    }
    stage('docker') {
      
      dockerBuildAndPush(this, this.imageNameWithUserid, this.credentials)
    }
    input "Proceed with deployment?"

    stage('docker deploy') {
      deployWithAnsible(this, host)
      }

    stage('send notification') {
        mail to: 'royraunak96@gmail.com', from: 'royraunak96@gmail.com',
                  subject: "Build: ${env.JOB_NAME} - Success", 
                  body: "Job Failed - \"${env.JOB_NAME}\" build: ${env.BUILD_NUMBER}"
    }
  } catch() {
    mail to: 'royraunak96@gmail.com', from: 'royraunak96@gmail.com',
                  subject: "Build: ${env.JOB_NAME} - Failed", 
                  body: "Job Failed - \"${env.JOB_NAME}\" build: ${env.BUILD_NUMBER}"
  }
}

