pipeline {
    agent any

    tools {
        maven 'maven'
        jdk 'jdk'
        nodejs 'nodejs'
    }

    environment {
        SCANNER_HOME = tool 'scanner'
    }

    stages {
        stage('1.0 Clean Workspace') {
            steps {
                cleanWs()
            }
        }

        stage('2.0 Git') {
            steps {
                git branch: 'main', url: 'https://github.com/FortressTechnologiesInc/10-MicroService-Appliction.git'
            }
        }

        stage('3.0 SonarQube Analysis') {
            steps {
                withSonarQubeEnv('sonar') {
                    sh "${SCANNER_HOME}/bin/sonar-scanner -Dsonar.projectKey=10-tier -Dsonar.projectName=10-tier -Dsonar.java.binaries=."
                }
            }
        }

        stage('4.0 adservice') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker', toolName: 'docker') {
                        dir('/root/appnode/workspace/10-tier/src/adservice/') {
                            sh "docker build -t limkel/adservice:2.0 ."
                            sh "trivy image limkel/adservice:2.0 > trivy-report.txt"
                            sh "docker push limkel/adservice:2.0"
                            sh "docker rmi -f limkel/adservice:2.0 "
                        }
                    }
                }
            }
        }

        stage('5.0 cartservice') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker', toolName: 'docker') {
                        dir('/root/appnode/workspace/10-tier/src/cartservice/src/') {
                            sh "docker build -t limkel/cartservice:2.0 ."
                            sh "trivy image limkel/cartservice:2.0 > trivy-report.txt"
                            sh "docker push limkel/cartservice:2.0"
                            sh "docker rmi -f limkel/cartservice:2.0"
                        }
                    }
                }
            }
        }

        stage('6.0 checkoutservice') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker', toolName: 'docker') {
                        dir('/root/appnode/workspace/10-tier/src/checkoutservice/') {
                            sh "docker build -t limkel/checkoutservice:2.0 ."
                            sh "trivy image limkel/checkoutservice:2.0 > trivy-report.txt"
                            sh "docker push limkel/checkoutservice:2.0"
                            sh "docker rmi -f limkel/checkoutservice:2.0"
                        }
                    }
                }
            }
        }

        stage('7.0 currencyservice') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker', toolName: 'docker') {
                        dir('/root/appnode/workspace/10-tier/src/currencyservice/') {
                            sh "docker build -t limkel/currencyservice:2.0 ."
                             sh "trivy image limkel/currencyservice:2.0 > trivy-report.txt"
                            sh "docker push limkel/currencyservice:2.0"
                            sh "docker rmi -f limkel/currencyservice:2.0" 
                        }
                    }
                }
            }
        }

        stage('8.0 emailservice') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker', toolName: 'docker') {
                        dir('/root/appnode/workspace/10-tier/src/emailservice/') {
                            sh "docker build -t limkel/emailservice:2.0 ."
                            sh "trivy image limkel/emailservice:2.0 > trivy-report.txt"
                            sh "docker push limkel/emailservice:2.0"
                            sh "docker rmi -f limkel/emailservice:2.0"
                        }
                    }
                }
            }
        }

        stage('9.0 frontend') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker', toolName: 'docker') {
                        dir('/root/appnode/workspace/10-tier/src/frontend/') {
                            sh "docker build -t limkel/frontend:2.0 ."
                             sh "trivy image limkel/frontend:2.0 > trivy-report.txt"
                            sh "docker push limkel/frontend:2.0"
                            sh "docker rmi -f  limkel/frontend:2.0"
                        }
                    }
                }
            }
        }

        stage('10 loadgenerator') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker', toolName: 'docker') {
                        dir('/root/appnode/workspace/10-tier/src/loadgenerator/') {
                            sh "docker build -t limkel/loadgenerator:2.0 ."
                            sh "trivy image limkel/loadgenerator:2.0 > trivy-report.txt"
                            sh "docker push limkel/loadgenerator:2.0"
                            sh "docker rmi -f limkel/loadgenerator:2.0"
                        }
                    }
                }
            }
        }

        stage('11 paymentservice') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker', toolName: 'docker') {
                        dir('/root/appnode/workspace/10-tier/src/paymentservice/') {
                            sh "docker build -t limkel/paymentservice:2.0 ."
                            sh "docker push limkel/paymentservice:2.0"
                             sh "trivy image limkel/paymentservice:2.0 > trivy-report.txt"
                            sh "docker rmi -f limkel/paymentservice:2.0"
                        }
                    }
                }
            }
        }

        stage('12 productcatalogservice') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker', toolName: 'docker') {
                        dir('/root/appnode/workspace/10-tier/src/productcatalogservice/') {
                            sh "docker build -t limkel/productcatalogservice:2.0 ."
                            sh "trivy image limkel/productcatalogservice:2.0 > trivy-report.txt"
                            sh "docker push limkel/productcatalogservice:2.0"
                            sh "docker rmi -f limkel/productcatalogservice:2.0"
                        }
                    }
                }
            }
        }

        stage('13 recommendationservice') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker', toolName: 'docker') {
                        dir('/root/appnode/workspace/10-tier/src/recommendationservice/') {
                            sh "docker build -t limkel/recommendationservice:2.0 ."
                             sh "trivy image limkel/recommendationservice:2.0 > trivy-report.txt"
                            sh "docker push limkel/recommendationservice:2.0"
                            sh "docker rmi -f limkel/recommendationservice:2.0"
                        }
                    }
                }
            }
        }

        stage('14 shippingservice') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker', toolName: 'docker') {
                        dir('/root/appnode/workspace/10-tier/src/shippingservice/') {
                            sh "docker build -t limkel/shippingservice:2.0 ."
                            sh "trivy image limkel/shippingservice:2.0 > trivy-report.txt"
                            sh "docker push limkel/shippingservice:2.0"
                            sh "docker rmi -f limkel/shippingservice:2.0"
                        }
                    }
                }
            }
        }
        stage('16 K8') {
            steps {
                withKubeConfig(caCertificate: '', clusterName: '', contextName: '', credentialsId: 'minikube', namespace: '10tier', restrictKubeConfigAccess: false, serverUrl: ' https://192.168.58.2:8443') {
                    sh "kubectl apply -f ./release/kubernetes-manifests.yaml"
                    sh "kubectl get pods -n 10tier"
                    sh "kubectl get svc -n 10tier"
                }
            }
        }
    }
}
