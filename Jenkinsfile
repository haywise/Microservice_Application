pipeline {
    agent any
    environment {
        SCANNER_HOME = tool 'sonar_scanner'

   }

    stages {
            stage('SonarQube') {
             steps {
                withSonarQubeEnv('sonar') {
                    sh '''$SCANNER_HOME/bin/sonar-scanner -Dsonar.projectKey=Microservice_Application -Dsonar.ProjectName=Microservice_Application -Dsonar.java.binaries=.'''
                }
            }
        }
            stage('adservice') {
              steps {
               script {
                 withDockerRegistry(credentialsId: 'dockerhub', toolName: 'docker') {
                    dir('/var/lib/jenkins/workspace/Microservice_Application/src/adservice/') {
                        sh "docker build -t haywise/adservice:latest ."
                        sh "docker push haywise/adservice:latest"
                        sh "docker rmi haywise/adservice:latest"
                    }
                }
            }
        }
            }
            stage('cartservice') {
              steps {
               script {
                 withDockerRegistry(credentialsId: 'dockerhub', toolName: 'docker') {
                    dir("/var/lib/jenkins/workspace/Microservice_Application/src/cartservice/src/") {
                        sh "docker build -t haywise/cartservice:latest ."
                        sh "docker push haywise/cartservice:latest"
                        sh "docker rmi haywise/cartservice:latest"
                    }
                }
            }
        }
       }
            stage('checkoutservice') {
              steps {
               script {
                 withDockerRegistry(credentialsId: 'dockerhub', toolName: 'docker') {
                    dir("/var/lib/jenkins/workspace/Microservice_Application/src/checkoutservice/") {
                        sh "docker build -t haywise/checkoutservice:latest ."
                        sh "docker push haywise/checkoutservice:latest"
                        sh "docker rmi haywise/checkoutservice:latest"
                    }
                }
            }
        }
            }
            stage('currencyservice') {
              steps {
               script {
                 withDockerRegistry(credentialsId: 'dockerhub', toolName: 'docker') {
                    dir("/var/lib/jenkins/workspace/Microservice_Application/src/currencyservice/") {
                        sh "docker build -t haywise/currencyservice:latest ."
                        sh "docker push haywise/currencyservice:latest"
                        sh "docker rmi haywise/currencyservice:latest"
                    }
                }
            }
        }

            }
            stage('emailservice') {
              steps {
               script {
                 withDockerRegistry(credentialsId: 'dockerhub', toolName: 'docker') {
                    dir("/var/lib/jenkins/workspace/Microservice_Application/src/emailservice/") {
                        sh "docker build -t haywise/emailservice:latest ."
                        sh "docker push haywise/emailservice:latest"
                        sh "docker rmi haywise/emailservice:latest"
                    }
                }
            }
        }
            }
            stage('frontend') {
              steps {
               script {
                 withDockerRegistry(credentialsId: 'dockerhub', toolName: 'docker') {
                    dir("/var/lib/jenkins/workspace/Microservice_Application/src/frontend/") {
                        sh "docker build -t haywise/frontend:latest ."
                        sh "docker push haywise/frontend:latest"
                        sh "docker rmi haywise/frontend:latest"
                    }
                }
            }
        }
            }
            stage('loadgenerator') {
              steps {
               script {
                 withDockerRegistry(credentialsId: 'dockerhub', toolName: 'docker') {
                    dir("/var/lib/jenkins/workspace/Microservice_Application/src/loadgenerator/") {
                        sh "docker build -t haywise/loadgenerator:latest ."
                        sh "docker push haywise/loadgenerator:latest"
                        sh "docker rmi haywise/loadgenerator:latest"
                    }
                }
            }
        }
            }
             stage('paymentservice') {
              steps {
               script {
                 withDockerRegistry(credentialsId: 'dockerhub', toolName: 'docker') {
                    dir("/var/lib/jenkins/workspace/Microservice_Application/src/paymentservice/") {
                        sh "docker build -t haywise/paymentservice:latest ."
                        sh "docker push haywise/paymentservice:latest"
                        sh "docker rmi haywise/paymentservice:latest"
                    }
                }
            }
        }
             }
             stage('productcatalogservice') {
              steps {
               script {
                 withDockerRegistry(credentialsId: 'dockerhub', toolName: 'docker') {
                    dir("/var/lib/jenkins/workspace/Microservice_Application/src/productcatalogservice/") {
                        sh "docker build -t haywise/productcatalogservice:latest ."
                        sh "docker push haywise/productcatalogservice:latest"
                        sh "docker rmi haywise/productcatalogservice:latest"
                    }
                }
            }
        }
             }
             stage('recommendationservice') {
              steps {
               script {
                 withDockerRegistry(credentialsId: 'dockerhub', toolName: 'docker') {
                    dir("/var/lib/jenkins/workspace/Microservice_Application/src/recommendationservice/") {
                        sh "docker build -t haywise/recommendationservice:latest ."
                        sh "docker push haywise/recommendationservice:latest"
                        sh "docker rmi haywise/recommendationservice:latest"
                    }
                }
            }
        }
             }
             stage('shippingservice') {
              steps {
               script {
                 withDockerRegistry(credentialsId: 'dockerhub', toolName: 'docker') {
                    dir("/var/lib/jenkins/workspace/Microservice_Application/src/shippingservice/") {
                        sh "docker build -t haywise/shippingservice:latest ."
                        sh "docker push haywise/shippingservice:latest"
                        sh "docker rmi haywise/shippingservice:latest"
                    }
                }
            }
        }
    }

              stage('EKS-Deployment') {
            steps {
                withKubeConfig(caCertificate: '', clusterName: 'myAppp-eks-cluster', contextName: '', credentialsId: 'k8s', namespace: 'webapps', restrictKubeConfigAccess: false, serverUrl: 'https://53754222F6B0B5A3A99E39613DFD4418.gr7.us-east-1.eks.amazonaws.com') {
                    sh 'kubectl apply -f deployment-service.yaml'
                    sh 'kubectl get pods'
                    sh 'kubectl get svc'

                }
                }
            }
        }
   }
