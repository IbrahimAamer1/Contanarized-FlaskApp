pipeline{
    agent{
        label 'agent1'
        //dasjkdasndas
    }
    stages{
        stage('build'){
            steps{
                sh "docker build -t ibrahimaamer/ibrahim:V${env.BUILD_NUMBER} ."
                withCredentials([usernamePassword(credentialsId: 'dockerhub-credentials', passwordVariable: 'pass', usernameVariable: 'user')]) {
                 sh "docker login -u $user -p $pass"
                 sh "docker push ibrahimaamer/ibrahim:V${env.BUILD_NUMBER}"
}              
            }
        }
        stage('deploy'){
            steps{
                sh "docker run -d -p 500${env.BUILD_NUMBER}:8080 ibrahimaamer/ibrahim:V${env.BUILD_NUMBER}"
            }
        }
    }
}
