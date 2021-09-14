node{
    def mavenHome = tool name:"maven3.8.2"
       echo "GitHub BranhName ${env.BRANCH_NAME}"
       echo "Jenkins Job Number ${env.BUILD_NUMBER}"
       echo "Jenkins Node Name ${env.NODE_NAME}"
  
       echo "Jenkins Home ${env.JENKINS_HOME}"
       echo "Jenkins URL ${env.JENKINS_URL}"
       echo "JOB Name ${env.JOB_NAME}"
    stage('CheckOutCode')
    {
    git branch: 'development', credentialsId: 'f7b13b02-b580-4572-b08a-879d546535ca', url: 'https://github.com/ca-ec-projects-practice/maven-web-application.git'
    }
    stage('Build')
    {
        sh "${mavenHome}/bin/mvn clean package"
    }
    /*
    stage('SonarQubeReport'){
        sh "${mavenHome}/bin/mvn clean sonar:sonar"
    }
    stage('UploadArtifactIntoNexus'){
        sh "${mavenHome}/bin/mvn clean deploy"
    }
    stage('DeployAppIntoTomcatServer')
    {
        sshagent(['4ed03261-f07f-4128-8407-9e1fb6c3bc09']) {
       sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@65.2.150.246:/opt/apache-tomcat-9.0.52/webapps/"

    }
    }
    */
    stage('sendEmailNotification'){
        emailext body: '''Build is over!!

Regards
Chanakya Academy
9293923576''', subject: 'Build Over...!!', to: 'chanakyadevops.jntu@gmail.com'
    }
}
