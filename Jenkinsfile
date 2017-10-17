#!groovy

def buildImage(name, directory) {
    withDockerRegistry([credentialsId: 'hub.docker.com']) {
        dir(directory) {
             def image
             stage('build') {
                image = docker.build(name)
             }
             stage('publish') {
                image.push "${env.BUILD_NUMBER}"
                image.push "latest"
             }
        }
    }
}


node {
    deleteDir()
    checkout scm
    buildImage('jcustenborder/packaging-centos-7', 'docker/packaging-centos-7')
    buildImage('jcustenborder/packaging-documentation', 'docker/packaging-documentation')
    buildImage('jcustenborder/packaging-ubuntu-17.04', 'docker/packaging-ubuntu-17.04')
    buildImage('jcustenborder/packaging-ubuntu-17.10', 'docker/packaging-ubuntu-17.10')
}

