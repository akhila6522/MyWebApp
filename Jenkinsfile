
pipeligene {
      agent any
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
      }
}
