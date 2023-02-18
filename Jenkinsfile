pipeline{


        agent  any


        environment{

                DOCKERHUB_USERNAME = "shriniwas34"
                  APP_NAME = "gitops-argo-app"
                  IMAGE_TAG = "${BUILD_NUMBER}"
                  IMAGE_NAME = "${DOCKERHUB_USERNAME}"  + "/" + "${APP_NAME}"
            REGISTRY_CREDS = 'dockerhub'





      }



            stages{



                stage('Cleanup workspace'){



                    steps{


                            script{

                                cleanWs()
                            }


                    }



                }



                stage('checkout scm'){






                        steps{

                            script{

                                git branch: 'main', credentialsId: 'github',
                                 url: 'https://github.com/shriniwas-devops/argocd.git'





                            }
                        }








                }



                 stage('Build Docker iamge'){



                   steps{



                          script{

                                   docker_image = docker.build "${IMAGE_NAME}"



                           }
                        }

                }


                 stage('Push Docker Image'){

                       steps{

                
                   script{


                               docker.withRegistry('',REGISTRY_CREDS){
                                docker_image.push("$BUILD_NUMBER")
                                 docker_image.push("latest")




                            }
            }


                          }
                       }



                       stage('Delete Docker Image'){

                        steps{


                            script{


                                sh "docker rmi ${IMAGE_NAME}:${IMAGE_TAG}"
                                sh "docker rmi ${IMAGE_NAME}:latest"
                            }
                        }
                       }

                }


             


                }




            

        

//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