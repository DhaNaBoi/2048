pipeline {
    agent {
        docker {
            // Specify the label associated with the Docker agent in Jenkins configuration
            label 'docker-agent'
            reuseNode true
        }
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building the JavaScript application...'
            }
        }

        stage('Deploy') {
            steps {
                script {
                    // Your Docker image should be pushed to a registry accessible by the Docker host
                    docker.image('first_app').pull()
                    docker.image('first_app').run()
                }
            }
        }
    }
}
