node{

def mavenHome = tool name: 'maven3.9.2'


echo "Job Name is : $JOB_NAME"
echo "Node Name is: $NODE_NAME"
echo "Jenkins Home Url is : $JENKINS_HOME"

properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')), [$class: 'JobLocalConfiguration', changeReasonComment: ''], pipelineTriggers([pollSCM('* * * * *')])])

stage('CheckOutCode'){
git branch: 'development', credentialsId: '03910f19-def9-465a-a019-86621452161f', url: 'https://github.com/Saijyothsna31/maven-web-application.git'
}

stage('Build'){
sh "${mavenHome}/bin/mvn clean package"
}
/*
stage('ExecuteSonarQubeReport'){
    sh "${mavenHome}/bin/mvn clean sonar:sonar"
}

stage('UploadArtifactsIntoNexus'){
    sh "${mavenHome}/bin/mvn clean deploy"
}

stage('DeployAppIntoTomcatServer')
sshagent(['3200bb59-e0cd-478a-ade0-b3b6138908d9']) {
    sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@172.31.37.72:/opt/apache-tomcat-9.0.75/webapps"
}
*/
}
