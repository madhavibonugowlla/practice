pipeline {
    agent any

    stages {
        stage('git_clone') {
            steps {
                sh '''
                echo 'cloning code from git'
                rm -rf practice
                git clone 'https://github.com/Sonushaik1143/practice.git'
                '''
            }
        }
        stage('BUILD') {
            steps {
                sh '''
                echo 'here compiling the dev code'
                pwd
                ls -ll
                cd practice
                mvn clean
                mvn compile
                '''
            }
        }
        stage('test') {
            steps {
                sh '''
                echo 'validating test cases'
                pwd
                ls -ll
                cd practice
                mvn test
                '''
            }
        }
      stage('sonar') {
            steps {
                sh '''
                echo 'validating sonar code coverage'
                pwd
                ls -ll
                cd practice
                mvn sonar:sonar
                '''
            }
        }
        stage('package') {
            steps {
                sh '''
                echo 'creating package'
                pwd
                ls -ll
                cd practice
                mvn package
                '''
            }
        }
        stage('jfrog') {
            steps {
            sh '''
            echo 'uploading packages to jfrog repo'
            curl -u admin:admin@123 -T /c/Users/Prabhu/.jenkins/workspace/pipeline_job/practice/target/com.google-google1.0.jar "http://localhost:8081/artifactory/devops-test/."

            '''
            }
        }
    }
}
