
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
    string(name: 'imageNameWithUserid', defaultValue: '47f84f4d-ab54-4743-8250-875b54c8bab9', description: '' ),
    string(name: 'credentials', defaultValue: '47f84f4d-ab54-4743-8250-875b54c8bab9', description: '' ),
    string(name: 'port1', defaultValue: '8003', description: '' ),
    string(name: 'port2', defaultValue: '8080', description: '' ),
    string(name: 'host', defaultValue: 'dev', description: '' )
   ])
])


// imageNameWithUserid = '47f84f4d-ab54-4743-8250-875b54c8bab9'
// credentials = '47f84f4d-ab54-4743-8250-875b54c8bab9'
// port1 = '8003'
// port2 = '8080'
// host = 'dev'

node('master') {
  //   stage('pull') {
  //       scmCheckout(this)
  //   }
  
  //   stage('sonar') {
  //       sonarAnalysis this, 'JDK 8', 'MAVEN_HOME'
  //   }
  //  stage('build') {
  //      buildWithMaven(this,  'JDK 8', 'MAVEN_HOME')
  //   //   withMaven (
  //   //     maven: 'MAVEN_HOME',
  //   //     jdk: 'JDK 8') {
  //   //     sh 'mvn clean install';
  //   //     } 
  //  }
  //  stage('docker') {
     
  //   dockerBuildAndPush(this, this.imageNameWithUserid, this.credentials)
  //  }
  // stage('email') {
  //   //emailextrecipients(['raunak.roy2@mindtree.com'])
  // }
  
  // input "Proceed with deployment?"
  
   stage('docker deploy') {
     deployWithAnsible(this, host)
       //dockerPullAndRun(this, this.imageNameWithUserid, this.credentials, this.port1, this.port2)
     //withCredentials([usernamePassword(credentialsId: '47f84f4d-ab54-4743-8250-875b54c8bab9', passwordVariable: 'dockerPassword', usernameVariable: 'dockerUsername')]) {
      // ansiblePlaybook(
      //  credentialsId: '43195002-dcf4-4397-bb78-adf4429b5968',  
      //  playbook: 'DeployDocker.yml', 
      //  extraVars: [
      //    HOST:this.host, USERNAME:env.dockerUsername, PASSWORD:env.dockerPassword
      //  ])
     // sh "ansible-playbook DeployDocker.yml -i inventory -vvvv --extra-vars 'HOST=${this.host} USERNAME=${env.dockerUsername} PASSWORD=${env.dockerPassword}'"
    //ansiblePlaybook credentialsId: '43195002-dcf4-4397-bb78-adf4429b5968', playbook: 'DeployDocker.yml'
   }
    }
    
}

