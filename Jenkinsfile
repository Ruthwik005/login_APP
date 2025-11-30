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
            echo '🎯 BUILD SUCCESS — All stages completed!'

            emailext (
                subject: "✅ Jenkins Build SUCCESS: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: """
                ✅ BUILD SUCCESSFUL!

                Job Name   : ${env.JOB_NAME}
                Build No   : ${env.BUILD_NUMBER}
                Status     : SUCCESS
                Build URL  : ${env.BUILD_URL}

                Regards,
                Jenkins Automation
                """,
                to: "kumaraswamybakkashetti@gmail.com"
            )
        }

        failure {
            echo '❌ BUILD FAILED!'

            emailext (
                subject: "❌ Jenkins Build FAILED: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: """
                ❌ BUILD FAILED!

                Job Name   : ${env.JOB_NAME}
                Build No   : ${env.BUILD_NUMBER}
                Status     : FAILED
                Build URL  : ${env.BUILD_URL}

                Please check immediately.
                """,
                to: "kumaraswamybakkashetti@gmail.com"
            )
        }
    }
}
