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


                stage('Git Checkout SCM'){

                    steps{

                            script{

                                git credentialsId: 'github',
                                url: 'https://github.com/shriniwas-devops/gitops_argocd-project.git',
                                branch: 'main'
                            }

                    }

                }



                }
            }

        


