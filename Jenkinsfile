node {
    stage("clone") {
        checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/jawadyousoufi/sharedtools.git']]])
    }
    stage("build") {
        sh "docker build -t tools ."
    }
}