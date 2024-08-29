node('built-in') {
    stage('ContinuousDownload') {
        git 'https://github.com/P2PConcept/maven.git'
}
    stage('ContinuousBuild') {
        sh 'mvn package'
}
    stage('ContinuousDeploy') {
        deploy adapters: [tomcat9(credentialsId: '9700724d-8f83-4d32-b7c9-8b5f88bda1d7', path: '', url: 'http://172.31.34.197:8080')], contextPath: 'testapplication', war: '**/*.war'
}
    stage('ContinuousTesting') {
        git 'https://github.com/P2PConcept/testingcode'
        sh 'java -jar /var/lib/jenkins/workspace/Scripted-Pipeline/testing.jar'
}
    stage('ContinuousDelivery') {
        deploy adapters: [tomcat9(credentialsId: '9700724d-8f83-4d32-b7c9-8b5f88bda1d7', path: '', url: 'http://172.31.36.67:8080')], contextPath: 'prodapplication', war: '**/*.war'
}
}
