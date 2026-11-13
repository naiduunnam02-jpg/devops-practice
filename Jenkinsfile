
pipeline {
    agent any

    stages {
        stage('Build Java Application') {
            steps {
                echo 'Building Java application...'
                sh '''
                    mkdir -p build
                    javac -d build java/HelloWorld.java
                    java -cp build HelloWorld
                '''
            }
        }

        stage('Deploy to Tomcat') {
            steps {
                echo 'Deploying application to Tomcat...'
                sh '''
                    cp -r myapp/. /var/lib/tomcat10/webapps/myapp/
                '''
            }
        }
    }
}
