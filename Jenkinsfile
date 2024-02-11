pipeline {
    agent {
        node {
            label 'maven'
        }
    }

    stages {
        stage('Hello') {
            steps {
                git branch: 'main', credentialsId: 'github_cred', url: 'https://github.com/snehal1306/tweet-trend-new.git'
            }
        }
    }
}
