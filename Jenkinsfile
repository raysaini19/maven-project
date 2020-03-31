pipeline {
    agent any
    parameters {
        string(name: 'tag_version', defaultValue: 'networn-01022010', description: 'release date buildno')
    }
    stages {
//        stage('Getting ready...') {
//                git branch: "dev", credentialsId: 'your_id_on_jenkins', url: 'https://github.com/Raysaini109/maven-project.git'
//              }
        stage('Declare') {
            steps {
                sh 'mvn --version'
            }
        }
        stage('Pre-Build') {
            steps {
                sh 'mvn clean'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests package'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Tagging'){
            steps{
                git tag -a ${BUILD_NUMBER}
                
            }
        }
    }
}
