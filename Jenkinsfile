pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
		stage('Ejemplo shell script') {
            agent { label 'docker-agent' }
			steps {
                sh 'echo "Hello World 2"'
                sh '''
					hostname
                    echo "Multiline shell steps works too"
                    ls -lah
					pwd
                '''
            }
        }
		stage ("Test") {
            when {
                branch "PR-*"
            }
            steps {
                sh "bash test.sh"
            }
        }
    }
}