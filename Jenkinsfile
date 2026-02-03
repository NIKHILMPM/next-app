pipeline{
    agent any

    environment{
        IMAGE_NAME = 'ramachandrampm/myapp'
    }

    stages{
        stage('checkout code'){
            steps{
                git branch: 'main',
                url: 'https://github.com/NIKHILMPM/next-app.git'
            }
        }

        stage('builddocker image '){
            steps{
                sh '''
                docker build -t $IMAGE_NAME .

                '''
            }
        }
        stage('build and push docker image in docker hub'){
            steps{
                withDockerRegistry([credentialsId: 'docker-creds', url: '']) {
                    sh 'docker push $IMAGE_NAME'
                }
            }
        }

    }
}