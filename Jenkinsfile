pipeline {
	agent none
   environment {
		DOCKERHUB_CREDENTIALS = credentials('dockerhub')
	}
  stages {
  	stage('Maven Install') {
    	agent {
      	docker {
        	image 'maven:3.5.0'
        }
      }
     
      steps {
      	sh 'mvn clean install'
      }
    }
    stage('Init'){
            agent any
            steps{
            sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
          }
  
  }
  stage('Build api-gateway-service') {
            agent any
            when {
                changeset "**/api-gateway-service/*.*"
                beforeAgent true
            }
            steps {
                dir('api-gateway-service'){
                    sh 'docker build -t $DOCKERHUB_CREDENTIALS_USR/api-gateway-service:$BUILD_ID .'
                    sh 'docker push $DOCKERHUB_CREDENTIALS_USR/api-gateway-service:$BUILD_ID'
                    sh 'docker rmi $DOCKERHUB_CREDENTIALS_USR/api-gateway-service:$BUILD_ID'
                    sh 'docker logout'
                }
            }
        }
        stage('Build eureka-service') {
            agent any
            when {
                changeset "**/eureka-service/*.*"
                beforeAgent true
            }
            steps {
                dir('eureka-service'){
                    sh 'docker build -t $DOCKERHUB_CREDENTIALS_USR/eureka-service:$BUILD_ID .'
                    sh 'docker push $DOCKERHUB_CREDENTIALS_USR/eureka-service:$BUILD_ID'
                    sh 'docker rmi $DOCKERHUB_CREDENTIALS_USR/eureka-service:$BUILD_ID'
                    sh 'docker logout'
                }
            }
        }
        stage('Build zuul-service') {
            agent any
            when {
                changeset "**/zuul-service/*.*"
                beforeAgent true
            }
            steps {
                dir('zuul-service'){
                    sh 'docker build -t $DOCKERHUB_CREDENTIALS_USR/zuul-service:$BUILD_ID .'
                    sh 'docker push $DOCKERHUB_CREDENTIALS_USR/zuul-service:$BUILD_ID'
                    sh 'docker rmi $DOCKERHUB_CREDENTIALS_USR/zuul-service:$BUILD_ID'
                    sh 'docker logout'
                }
            }
        }

  }
}