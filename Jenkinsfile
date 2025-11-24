pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/KumaraswamyBakkashetti/login-app2.git'
            }
        }

        stage('Deploy to Tomcat') {
            steps {
                bat """
                if not exist "C:\\apache-tomcat-9.0.112\\webapps\\loginapp" mkdir "C:\\apache-tomcat-9.0.112\\webapps\\loginapp"
                xcopy /Y /E C:\\ProgramData\\Jenkins\\.jenkins\\workspace\\loginapp\\* C:\\apache-tomcat-9.0.112\\webapps\\loginapp\\
                """
            }
        }
    }
}
