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
                echo Deploying to Tomcat...
                if not exist "C:\\apache-tomcat-9.0.112\\webapps\\loginapp" mkdir "C:\\apache-tomcat-9.0.112\\webapps\\loginapp"
                xcopy /Y /E "%WORKSPACE%\\*" "C:\\apache-tomcat-9.0.112\\webapps\\loginapp\\"
                echo Deployment Completed!
                """
            }
        }
    }

    post {
        success {
            emailext(
                mimeType: 'text/html; charset=UTF-8',
                subject: "SUCCESS: Login App Deployment #${env.BUILD_NUMBER}",
                body: """
                <h2 style='color:green;'>✔ Deployment Successful</h2>
                <p><b>Project:</b> ${env.JOB_NAME}</p>
                <p><b>Build Number:</b> #${env.BUILD_NUMBER}</p>
                <p><b>Status:</b> SUCCESS</p>
                <p><a href='${env.BUILD_URL}'>View Build Details</a></p>
                <p>UTF-8 Test: Hello 🌍 — नमस्ते — こんにちは — مرحبا — 🙂</p>
                """,
                to: "kumaraswamybakkashetti@gmail.com"
            )
        }
        failure {
            emailext(
                mimeType: 'text/html; charset=UTF-8',
                subject: "FAILED: Login App Deployment #${env.BUILD_NUMBER}",
                body: """
                <h2 style='color:red;'>❌ Deployment Failed</h2>
                <p><b>Project:</b> ${env.JOB_NAME}</p>
                <p><b>Status:</b> FAILURE</p>
                <p>Please check logs here:</p>
                <p><a href='${env.BUILD_URL}console'>Console Log</a></p>
                <p>UTF-8 Test: 😕⚠️</p>
                """,
                to: "kumaraswamybakkashetti@gmail.com"
            )
        }
    }
}
