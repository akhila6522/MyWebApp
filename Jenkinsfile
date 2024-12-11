
pipeline {
      agent any
      
      environment {
            TOMCAT_URL='http://localhost:8081/manager/text'
            TOMCAT_USER='tomcat'
            TOMCAT_PASSWORD='12345'
            WAR_FILE='target/MyWebApp.war'
            DEPLOY_CONTEXT='/MyWebApp'
      }
      
      stages {
            stage('checkout') {
                  steps {
                        // Clone the repository
                        git branch: 'main', url: 'https://github.com/akhila6522/MyWebApp.git'
                  }
            }
            stage('build') {
                  steps {
                        // Use Maven to clean and package the application
                        sh 'mvn clean package'
                  }
            }
            stage("deploy to tomcat") {
                  steps {
                        script {
                            // Deploy the WAR file to Tomcat
                          sh """
                          curl --upload-file ${WAR_FILE} \
                              --user ${TOMCAT_USER}:${TOMCAT_PASSWORD} \
                              ${TOMCAT_URL}/deploy?path=${DEPLOY_CONTEXT}&update=true || true
                          """
                        }
                  }
            }            
      }
}
