pipeline {
    agent any

    stages {
        stage('Clone Code') {
            git branch: 'main', url: 'https://github.com/KumaraswamyBakkashetti/login-app2.git'

        }

        stage('Deploy to Tomcat') {
            steps {
                bat '''
                if not exist "C:\\Program Files\\Apache Software Foundation\\Tomcat 11.0\\webapps\\loginapp" mkdir "C:\\Program Files\\Apache Software Foundation\\Tomcat 11.0\\webapps\\loginapp"
                xcopy /Y /E "%WORKSPACE%\\*" "C:\\Program Files\\Apache Software Foundation\\Tomcat 11.0\\webapps\\loginapp"
                '''
            }
        }
    }
}

