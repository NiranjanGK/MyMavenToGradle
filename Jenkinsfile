pipeline {
agent any

tools {
    gradle 'Gradle'
    jdk 'JDK'
}

stages {
    stage('Checkout') {
        steps {
            git branch: 'master', url: 'https://github.com/sumanthr27/MyMavenToGradle.git'
        }
    }

    stage('Build') {
        steps {
            sh 'gradle clean build'
        }
    }

    stage('Test') {
        steps {
            sh 'gradle test'
        }
    }

    stage('Run Application') {
        steps {
            // Run the generated JAR file instead of gradle run
            sh 'java -jar build/libs/*.jar'
        }
    }
}

post {
    success {
        echo 'Build and deployment successful!'
    }
    failure {
        echo 'Build failed!'
    }
}

}
