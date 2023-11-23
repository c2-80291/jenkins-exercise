pipeline {
    agent any

    stages {
        stage ('SCM') {
            steps {
                git branch: 'master', url: 'https://github.com/c2-80291/jenkins-exercise.git'
            }
        }    
        stage ('docker login'){
            steps {
                sh 'echo dckr_pat_bzZSig1T_kt9k7eTNiS2ZgusGF4 | /usr/bin/docker login -u akmaster --password-stdin'
            }
        }
        stage ('docker image build'){
            steps {
                sh '/usr/bin/docker image build -t akmaster/mywebsite .'
            }
        }
        stage (' docker image push'){
            steps {
                sh '/usr/bin/docker image push akmaster/mywebsite'
            }
        }
        stage ('remove the service'){
            steps{
                sh '/usr/bin/docker service rm myservice'
            }
        }
        stage ('create a service'){
            steps{
                sh '/usr/bin/docker service create --name myservice --replicas=5 -p 9000:80 akmaster/mywebsite '
            }
        }
    }
}


