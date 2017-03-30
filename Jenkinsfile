pipeline{
    agent{
        label any
    }    
    stages{
        stage('Git clone or Pull'){
            steps{
                git 'https://github.com/spring-projects/spring-petclinic.git'
            }
        }
        stage('Build'){
            steps{
                sh 'mvn clean package'
            }
        }
        stage('Publish'){
            steps{
                archiveArtifacts 'target/spring-petclinic-1.5.1.jar'
                junit 'target/surefire-reports/*.xml'
            }
        }
    }

    post {
        success {
          emailext(
            subject: "${env.JOB_NAME} [${env.BUILD_NUMBER}] Development Promoted to Master",
            body: """<p>'${env.JOB_NAME} [${env.BUILD_NUMBER}]' Development Promoted to Master":</p>
            <p>Check console output at &QUOT;<a href='${env.BUILD_URL}'>${env.JOB_NAME} [${env.BUILD_NUMBER}]</a>&QUOT;</p>""",
            to: "bethalasuresh@gmail.com"
          )
        }
   
        failure {
        emailext(
            subject: "${env.JOB_NAME} [${env.BUILD_NUMBER}] Failed!",
            body: """<p>'${env.JOB_NAME} [${env.BUILD_NUMBER}]' Failed!":</p>
            <p>Check console output at &QUOT;<a href='${env.BUILD_URL}'>${env.JOB_NAME} [${env.BUILD_NUMBER}]</a>&QUOT;</p>""",
            to: "bethalasuresh@gmail.com"
        )
        }
    }
}

