pipeline {
    agent { label 'master' }

    stages {
        stage('Build') {
            steps {
                script {
                    echo 'Building..'

                    //#Ejecuci[on de Compress de carpeta del artefacto final tipo zip

                    
                    sh ('tar -cvf FreeStyle.zip /var/jenkins_home/workspace/FREESTILE/')
                    sh ('find $workspace -name FreeStyle.tar ')
                    echo "workspace: $workspace"
                }

            }
        }
        stage ('Jfrog'){
            steps {
              script {
                
                echo "pruebas "
                 // Upload Artifactory
                 rtUpload ( serverId: serverjfrog,
                            spec: '''{ "files": [ {
                                            "pattern": "$workspace/FreeStyle.tar",
                                            "target": "CursoIAC/QA/",
                                            "recursive": "false"
                                    }
                                ]
                            }'''
                        )
              }
            }
        }
    }
}