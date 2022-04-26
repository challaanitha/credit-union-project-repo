pipeline {
agent any
stages {
stage('Maven Compile'){
steps{
echo 'Project compile stage'

bat label: 'Compilation running', script: '''mvn -f credit-union-project/pom.xml compile'''
}
}

stage('Unit Test') {
steps {
echo 'Project Testing stage'
bat label: 'Test running', script: '''mvn -f credit-union-project/pom.xml test'''

}
}



stage('Jacoco Coverage Report') {
steps{
jacoco()
}
}

stage('SonarQube'){
steps{
bat label: '', script: '''mvn -f credit-union-project/pom.xml sonar:sonar \
-Dsonar.host.url=http://localhost:9000 \
-Dsonar.login=c9a66d657a514149bdb1b96bb8fcba1c'''
}
}

stage('Maven Package'){
steps{
echo 'Project packaging stage'
bat label: 'Project packaging', script: '''mvn -f credit-union-project/pom.xml package'''
}
}

}
}

