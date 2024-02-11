pipeline {
    agent {
        node {
            label 'maven'
        }
    }

    stages {
        stage('git-checkout') {
            steps {
                git branch: 'main', credentialsId: 'github_cred', url: 'https://github.com/snehal1306/tweet-trend-new.git'
            }
        }
	stage('build') {
            steps {
                sh 'mvn clean deploy'
            }
        }
    }
}
