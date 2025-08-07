pipeline {
    agent any

    environment {
        JAVA_HOME = '/usr/lib/jvm/java-17-openjdk-amd64' // adjust if different
        PATH = "${env.JAVA_HOME}/bin:${env.PATH}"
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/sivauser2001/my-java-app.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mkdir -p out'
                sh 'javac -d out src/Main.java'
            }
        }

        stage('Run') {
            steps {
                sh 'java -cp out Main'
            }
        }

        stage('Package') {
            steps {
                sh 'jar cvfe out/my-java-app.jar Main -C out .'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Simulating deploy...'
                sh 'ls -lh out/my-java-app.jar'
            }
        }
    }

    post {
        success {
            echo 'Java pipeline finished successfully!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
