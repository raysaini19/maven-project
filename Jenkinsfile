pipeline {
    agent any
    parameters {
        string(name: 'tag_version', defaultValue: 'networn-01022010', description: 'release date buildno')
    }
    stages {
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
               // sh("git config user.email ${repositoryCommiterEmail}")
               // sh("git config user.name '${repositoryCommiterUsername}'")

               //sh "git remote set-url origin git@github.com:..."

                // deletes current snapshot tag
                sh "git tag -d snapshot || true"
                // tags current changeset
                sh "git tag -a snapshot -m \"passed CI\""
                // deletes tag on remote in order not to fail pushing the new one
                //sh "git push origin :refs/tags/snapshot"
                // pushes the tags
                //sh "git push --tags"

            }
        }
    }
}
