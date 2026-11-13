pipeline {
    agent any

    stages {
        stage('Build Java Application') {
            steps {
                echo 'Building Java application...'
                sh '''
                    mkdir -p build
                    javac -d build java/HelloWorld.java
                '''
            }
        }

        stage('Test Java Application') {
            steps {
                echo 'Testing Java application...'
                sh '''
                    output=$(java -cp build HelloWorld)
                    echo "$output"
                    echo "$output" | grep -q "Hello DevOps!"
                    echo "Test passed successfully!"
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
