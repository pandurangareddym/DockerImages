node {
        deff app
        stage('Clone Repository') {
                checkout scm
        }

        stage('Build Image') {
                app = docker.build('pandureddym/python-hello-world1')
        }

        stage('Test Image') {
                app.inside {
                        echo "Tests Passed"
                }
        }

        stage('Push Image') {
                docker.withRegistry('https://registry.hub.docker.com','docker-hub') {
                        app.push("${env.BUILD_NUMBER}")
                        app.push("latest")
                }
                echo "Trying to push Docker image BUID"
        }
}

