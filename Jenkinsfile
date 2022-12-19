pipeline {
    agent { label 'master' }

    stages {
        stage('Build') {
            steps {
                echo 'Building..'

                //#Ejecuci[on de Compress de carpeta del artefacto final tipo zip

                
                sh ('tar -cvf FreeStyle.zip /var/jenkins_home/workspace/FREESTILE/')
                sh ('find $workspace -name FreeStyle.tar ')
                echo "workspace: $workspace"

            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                scritp {
                echo 'Deploying....'

                // Upload Artifactory
                 rtUpload (  serverId: JfrogServerID,
                            spec: '''{ "files": [ {
                                            "pattern": "FreeStyle.tar",
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