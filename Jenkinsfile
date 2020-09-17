pipeline {
    agent {
        docker {
            image 'adoptopenjdk/maven-openjdk11:latest'
            args '-v $HOME/.m2:/root/.m2'
        }
    }

    /* Store only 5 latest jobs on Jenkins */
    options { buildDiscarder(logRotator(numToKeepStr: '5')) }

    stages {
        stage("Build") {
            steps {
                sh 'mvn clean install'
            }
        }
    }
    post {
        cleanup {
            cleanWs()
        }
    }
}