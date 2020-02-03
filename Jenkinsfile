node('docker') {

  stage 'Checkout'
    checkout scm

  stage 'Build & UnitTest'
    sh "docker build -t aakashgoel/docker-react-jenkins -f Dockerfile.dev ."

  stage 'Integration Test'
    sh "docker run aakashgoel/docker-react-jenkins npm run test:coverage"
}
