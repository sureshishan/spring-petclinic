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
                sh 'mvn clean install'
            }
        }
        stage('Publish'){
            steps{
                archiveArtifacts 'target/spring-petclinic-1.5.1.jar'
                junit 'target/surefire-reports/*.xml'
            }
        }
    }
}

