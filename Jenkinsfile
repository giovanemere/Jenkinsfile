pipeline {
    agent { label 'master' }

    stages {
        stage('Build') {
            steps {
                script {
                    echo 'Building..'

                    //#Ejecuci[on de Compress de carpeta del artefacto final tipo zip

                    
                    sh ('tar -cvf FreeStyle.tar /var/jenkins_home/workspace/FREESTILE/')
                    sh ('find $workspace -name FreeStyle.tar ')
                    echo "workspace: $workspace"
                }

            }
        }
        stage ('Jfrog'){
            steps {
              script {
                
                echo "pruebas "
                env.FileArtifact = "${workspace}/FreeStyle.tar"
                env.JfrogServerID = "serverjfrog" 
                 // Upload Artifactory
                 rtUpload ( serverId: JfrogServerID,
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