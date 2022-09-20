node {
  def mavenHome = tool name: 'maven3.8.6'
  stage('1cloneCode'){
      
    git "https://github.com/samuelofochukwu/tesla-app.git"      
  }
  
  stage('2Test&Build'){
      
    sh "${mavenHome}/bin/mvn clean package"
  }
  
  stage('3codeQuality'){
      
      sh "${mavenHome}/bin/mvn sonar:sonar"
  }
  
  stage('4uploadArtifacts'){
      
      sh  "${mavenHome}/bin/mvn deploy"
  }
  
  stage('5deploy2UAT'){
      
      sh " echo 'deploy to UAT'"
      
      deploy adapters: [tomcat9(credentialsId: 'tomcatCredentials', path: '', url: 'http://54.211.146.132:8080/')], contextPath: null, war: 'target/*war'
      
  }
      
  stage('6approvalGate'){
      
      sh "echo 'ready for review' "
      timeout(time:5, unit:'DAYS'){
      input message: 'Application ready for deployment, Please review and approve'
      }
  }
      
    stage('5deploy2Prod'){
      
      sh " echo 'deploy to Prod'"
      
      deploy adapters: [tomcat9(credentialsId: 'tomcatCredentials', path: '', url: 'http://54.211.146.132:8080/')], contextPath: null, war: 'target/*war'
    }
    
    stage('8emailNotification'){
        
        emailext body: '''Hi All,

Check Build status.


Elsampee Services ''', recipientProviders: [buildUser(), developers(), upstreamDevelopers(), brokenBuildSuspects(), contributor()], subject: 'build status', to: 'tesla-app@gmail.com,sampee7@yahoo.com'
    }
    
}
