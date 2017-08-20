pipeline {
    agent any

    stages {
        stage('Test') {
            steps {
                echo 'Testing..'
                make deps
                make test
                make kafkatohip.out
            }
        }
        stage('Build') {
            steps {
                echo 'Building..'
                make silent-test
                make bin/docker-kafkatohip
                make bin/.docker-kafkatohip
            }
        }
        stage('Publish') {
            steps {
                echo 'Publishing....'
                echo 'Do we need some type of version taging ?'
                docker tag kafkatohip registry.dev.benon.com:5000/kafkatohip
                docker push registry.dev.benon.com:5000/kafkatohip
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
                echo 'As you have done your tests you should now be safe to automaticly deploy to staging and production'
                echo 'this should be done now as Jumbo values your effort'
                echo 'and would like to enjoy the value you have just added'
                echo 'Deploy to team staging site .. with some auto foo'
                echo 'Deploy to live  .. with some auto foo'
                echo ''
                echo 'If you used ansiable to deploy did you look at http://docs.ansible.com/ansible/latest/hipchat_module.html'
                echo 'I think this is the compose to update a running docker ?'
                echo 'docker-compose kill -s SIGINT                     # graceful stop of the current container'
                echo 'sleep 1                                           # need to wait for it to stop, maybe use the docker API?'
                echo 'docker-compose up -d --no-deps --build kafkatohip # update and start'
            }
        }
    }
}
