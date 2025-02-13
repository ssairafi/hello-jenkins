pipeline {
  agent any
  tools {
    maven "m3"
  }
  triggers {
    githubPush() // Automatically triggers on GitHub push events
  }
  stages {
    stage('Checkout Code') {
      steps {
        git branch: 'main', url: 'https://github.com/ssairafi/hello-jenkins.git'
      }
    }
    
    stage('Build with Maven') {
      steps {
        sh "mvn clean package -DskipTests"
      }
    }
  }
  post {
    always {
      archiveArtifacts 'target/*.jar' // Only archive the JAR file
    }
  }
}