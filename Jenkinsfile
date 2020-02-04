node {
  def app

  stage('Clone repository') {
    checkout scm
  }

  stage('Build Image') {
    sh "docker build -t aakashgoel/docker-react-jenkins -f Dockerfile.dev ."
  }

  stage('Test Image') {
    sh "docker run aakashgoel/docker-react-jenkins npm run test:coverage"
  }

  stage('Slack Notification') {
    slackSend(channel: "#jenkins-pipeline" color: "good", message: "SUCCESS: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' (${env.BUILD_URL})")
  }
}
