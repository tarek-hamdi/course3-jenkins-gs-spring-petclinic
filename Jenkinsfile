pipeline {
    agent any
    stages {
#        stage('checkout') {
#            steps {
#                sh 'rm -rf course3-jenkins-gs-spring-petclinic'
#                sh 'git clone https://github.com/g0t4/course3-jenkins-gs-spring-petclinic.git'
#                
#            }
#        }
        stage('build') {
            steps {
                sh 'cd course3-jenkins-gs-spring-petclinic && ./mvnw package'
            }
        }
        stage('Capture_Artifacts') {
            steps {
                archiveArtifacts artifacts: '**/target/*.jar'
                jacoco()
                junit stdioRetention: '', testResults: '**/target/surefire-reports/*.xml'
            }
        }
    }
    post {
        always {
        mail bcc: '', body: 'Check ya basha', cc: '', from: '', replyTo: '', subject: '\'$JOB_NAME\' , \'$BUILD_NUMBER\'', to: 'trk_hamdi@yahoo.com'
        }
    }
}
