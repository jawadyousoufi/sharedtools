node {
    stage("clone") {
        checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/jawadyousoufi/sharedtools.git']]])
    }
    stage("build") {
        sh "docker build -t tools ."
    }
    stage("tagging") {
        sh "docker tag tools:latest 667457604412.dkr.ecr.us-east-1.amazonaws.com/tools:latest"
    }
}