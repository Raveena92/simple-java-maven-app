pipeline {
    agent any
    environment {
        MAVEN_HOME = '/opt/apache-maven-3.9.9'  // Set this to your Maven installation path
        PATH = "$MAVEN_HOME/bin:$PATH"      // Add Maven bin directory to PATH
    }
    stages {
        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
        stage('Deliver it') {
            steps {
                sh './jenkins/scripts/deliver.sh'
            }
        }
        stage('complete') {
          steps {
                echo "this is completed"
            }
        }
    }
}
