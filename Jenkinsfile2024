node{

echo "Jenkins Home dir is: ${env.JENKINS_HOME}"
echo "Jenkins job name is: ${env.JOB_NAME}"
echo "Build number is: ${env.BUILD_NUMBER}"

properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')), [$class: 'RebuildSettings', autoRebuild: false, rebuildDisabled: false], [$class: 'JobLocalConfiguration', changeReasonComment: ''], pipelineTriggers([pollSCM('* * * * *')])])

def mavenHome=tool name: 'maven3.9.3'

stage('CheckOutCode'){
git branch: 'development', credentialsId: 'c8d1acaf-9ad0-4e9d-b1e9-882ebd517445', url: 'https://github.com/sathvikdevops2024/maven-web-application.git'
}

stage('Build'){
sh "${mavenHome}/bin/mvn clean package"
}
/*
stage('ExecuteSonarQubeReport'){
sh "${mavenHome}/bin/mvn clean sonar:sonar"
}

stage('UplpadArtifactsIntoNexus'){
sh "${mavenHome}/bin/mvn clean deploy"
}

stage('DeployAppIntoTomcatServer'){
sshagent(['4cc9784f-37b9-4bf0-882d-00fd4530cb14']) {
    sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@172.31.3.12:/opt/apache-tomcat-9.0.89/webapps/"
}
}
*/
}
