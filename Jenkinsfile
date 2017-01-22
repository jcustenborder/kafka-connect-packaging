#!groovy

def buildImage(name, directory) {
    withDockerRegistry([credentialsId: 'hub.docker.com']) {
        dir(directory) {
             def image
             stage('build') {
                image = docker.build(name)
             }
             stage('publish') {
                app.push "${env.BUILD_NUMBER}"
             }
        }
    }
}

parallel 'packaging-centos-6': {
    node {
        buildImage('packaging-centos-6', 'docker/packaging-centos-6')
    }
}, 'packaging-centos-7': {
    node {
        buildImage('packaging-centos-7', 'docker/packaging-centos-7')
    }
}

