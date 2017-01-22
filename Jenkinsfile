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

parallel 'packaging-centos-6': {
    node {
        checkout scm
        buildImage('jcustenborder/packaging-centos-6', 'docker/packaging-centos-6')
    }
}, 'packaging-centos-7': {
    node {
        checkout scm
        buildImage('jcustenborder/packaging-centos-7', 'docker/packaging-centos-7')
    }
}

