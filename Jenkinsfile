pipeline {
environment {
registry = "sivasobh/sivalab"
registryCredential = 'sivasobh.p@gmail.com'
dockerImage = ''
}
agent any
stages {
stage('Cloning our Git') {
steps {
git clone 'https://github.com/sivalabcodes/dockerpipline.git'
}
}
stage('Building our image') {
steps{
script {
dockerImage = docker.build registry + ":$BUILD_NUMBER"
}
}
}
stage('Deploy our image') {
steps{
script {
docker.withRegistry( '', registryCredential ) {
dockerImage.push()
}
}
}
}
stage('Cleaning up') {
steps{
sh "docker rmi $registry:$BUILD_NUMBER"
}
}
}
}
