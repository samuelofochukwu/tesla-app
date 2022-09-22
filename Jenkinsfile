pipeline{
    
    agent any
    
    tools{
        
        maven "maven3.8.6"
    }
    
    stages{
        
        stage('1GetCode'){
            steps{
                sh "echo 'cloning the latest application version'"
                git branch: 'feature', credentialsId: 'gitHubCredentials', url: 'https://github.com/samuelofochukwu/tesla-app'
            }
        }
        
        stage('2Test+Build'){
            steps{
                sh "echo 'running JUnit-test-cases' "
                sh " echo 'testing must pass to create artifacts  '"
                sh "mvn clean package"
            }
        }
        /*
        stage('3CodeQuality'){
            steps{
                sh "echo 'performing CodeQualityAnalysis' "
                sh "mvn sonar:sonar"
            }
        }
        
        stage('4UploadNexus'){
            steps{
                sh "echo 'Uploading artifact to Nexus' "
                sh "mvn deploy"
            }
        }
        
        stage('5Deploy2prod'){
            steps{
                sh "echo 'deploying to production'"
                deploy adapters: [tomcat9(credentialsId: 'tomcatCredentials', path: '', url: 'http://34.205.146.208:8080/')], contextPath: null, war: 'target/*war'
            }
        }
    }
    
    post{
        always{
            emailext body: '''Hey guys,
Please check status.

Thanks

Elsampee
+1 437 215 2483''', recipientProviders: [buildUser(), developers()], subject: 'success', to: 'paypal-team@gmail.com'
        }
        success{
            emailext body: '''Hey guys,
Good job! build and deployment is successful

Thanks

Elsampee
+1 437 215 2483''', recipientProviders: [buildUser(), developers()], subject: 'success', to: 'paypal-team@gmail.com'
        }
        failure{
            emailext body: '''Hey guys,
Build failed , please resolve issues.

Thanks

Elsampee
+1 437 215 2483''', recipientProviders: [buildUser(), developers()], subject: 'success', to: 'paypal-team@gmail.com'
        }
    }
   */ 
}
