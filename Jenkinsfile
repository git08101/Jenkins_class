node {
    stage('Continuous Download') {
    git 'https://github.com/git08101/maven.git'
}
stage('Continuous Build') {
    sh 'mvn package'
}
stage('Continuous Deployment') {
    sshagent(['ssh_ubuntu']) {
    sh 'scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/ScriptedPipeline/webapp/target/webapp.war ubuntu@172.31.11.161:/var/lib/tomcat8/webapps/qaenv.war'
}
}
stage('Continuous Testing') {
    sh 'echo (test success)'
}
stage('Continuous Delivery') {
    sshagent(['ssh_ubuntu']) {
    sh 'scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/ScriptedPipeline/webapp/target/webapp.war ubuntu@Production_IP:/var/lib/tomcat8/webapps/qaenv.war'
}
}