pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/Hareesha123/Java-codes.git'
                echo "checkout source code"
            }
        }
        
        stage('build') {
            steps {
                sh mvn clean install
                echo "Build stage success"
            }
        }
        
        stage('Upload artifact to nexus repo') {
            steps {
                'nexusArtifactUploader artifacts: [
					[
						artifactId: 'hello-world-war', 
						classifier: '', 
						file: 'target/hello-world-war-1.0.0.war', 
						type: 'war'
					]
				], 
				credentialsId: 'nexus3', 
				groupId: 'com.efsavage', 
				nexusUrl: '172.31.12.132', 
				nexusVersion: 'nexus3', 
				protocol: 'http', 
				repository: 'http://43.204.144.6:8081/repository/simpleapp_release', 
				version: '1.0.0''
            }
        }
    }
}
