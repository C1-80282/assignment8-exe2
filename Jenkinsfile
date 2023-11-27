pipeline {
    agent any

    stages {
        stage ('SCM') {
            steps {
                git branch: 'master', url: 'https://github.com/C1-80282/assignment8-exe2.git'
            }
        }
        stage ('docker login') {
            steps {
                sh 'echo dckr_pat_qoge6wgIk0ZER9upIo4ZhaOD0zg | /usr/bin/docker login -u heenashinganjude --password-stdin'
            }
        }
        stage ('docker build image') {
            steps {
                sh '/usr/bin/docker image build -t heenashinganjude/website2 .'
            }
        }
        stage ('docker push image') {
            steps {
                sh '/usr/bin/docker image push heenashinganjude/website2'
            }
        }
        stage ('docker remove service') {
            steps {
                sh '/usr/bin/docker service rm service2'
            }
        }
        stage ('docker create service') {
            steps {
                sh '/usr/bin/docker service create --name service2 -p 9091:80 --replicas 5 heenashinganjude/website2'
            }
        }
    }
}
