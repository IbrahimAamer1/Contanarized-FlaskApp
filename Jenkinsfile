pipeline{
    agent{
        label 'agent1'
        //dasjkdasndas
    }
    stages{
        stage('build'){
            steps{
                sh "docker build -t IbrahimAamer1/ibrahim:V${env.BUILD_NUMBER} ."
                withCredentials([usernamePassword(credentialsId: 'dockerhub', passwordVariable: 'pass', usernameVariable: 'user')]) {
                 sh "docker login -u $user -p $pass"
                 sh "docker push ibrahimaamer/test:V${env.BUILD_NUMBER}"
}              
            }
        }
        stage('deploy'){
            steps{
                sh "docker run -d -p 500${env.BUILD_NUMBER}:8080 maro4299311/marwan:V${env.BUILD_NUMBER}"
            }
        }
    }
}
