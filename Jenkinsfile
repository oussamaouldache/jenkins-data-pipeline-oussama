pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/oussamaouldache/jenkins-data-pipeline-oussama.git'
            }
        }
        stage('Build') {
            steps {
                script {
                    if (isUnix()) {
                        withEnv([
                            "JAVA_HOME=/usr/bin",
                            "PATH=${env.PATH}:/usr/bin"
                        ]) {
                            sh 'echo "Running on Unix"'
			    sh 'pip install pandas'
                            sh 'python3 data_analysis.py'
                        }
                    } else {
                        withEnv([
                            "JAVA_HOME=C:\\Program Files\\Java\\jdk1.8.0_202",
                            "PYTHON_HOME=C:\\Users\\rehou\\AppData\\Local\\Microsoft\\WindowsApps",
                            "PATH=%JAVA_HOME%\\bin;%PYTHON_HOME%;%PATH%"
                        ]) {
                            bat 'echo "Running on Windows"
                            bat 'python data_analysis.py'
                        }
                    }
                }
            }
        }
    }
}
