properties([parameters([string(defaultValue: '713287746880', description: 'Please provide your AWS account ', name: 'AWS_ACCOUNT', trim: true)])])



node {
    stage("Clone") {
        checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/farrukh90/shared_tools.git']]])
    }   
    stage("Build"){
        sh "docker build -t tools . "   // github.com/farrukh90/shared_tools.git
    }
    stage("Tagging"){
        sh "docker tag tools:latest ${AWS_ACCOUNT}.dkr.ecr.us-east-1.amazonaws.com/tools:latest"
    }
    stage("Authenticate"){
        sh "aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin ${AWS_ACCOUNT}.dkr.ecr.us-east-1.amazonaws.com"
    }
    stage("Push Image"){
        sh "docker push ${AWS_ACCOUNT}.dkr.ecr.us-east-1.amazonaws.com/tools:latest"
    }
    stage("Email") {
        sh "echo hello" //"/email"
    }
}






// node {
//     Clone 
//     Build 
//     Tagging
//     Authentication 
//     Push 
//     Email 
// }