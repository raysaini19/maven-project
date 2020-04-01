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
            environment{
                GIT_CRED = credentials('jenkins_github')
            }
            steps{
                sh """
                git config --global user.name "raysaini19"
                git config --global user.email "109manojsaini@gmail.com"
                
                git tag -d snapshot || true
                git tag -a snapshot -m \"passed CI\"
                git push origin :refs/tags/snapshot
                git push --tags

                git push https://$jenkins_github@https://github.com/Raysaini109/maven-project.git
                """
            }
        }
    }
}
