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



                stage{



                        steps{



                            script{

                                    docker_image = docker.build "${IMAGE_NAME}"



                            }
                        }

                }


             


                }
            }

        


