pipeline {
    agent { label 'master' }

    stages {
        stage('Build') {
            steps {
                echo 'Building..'

                //#Ejecuci[on de Compress de carpeta del artefacto final tipo zip
                sh ('/bin/zip -r "FreeStyle.zip" "/var/jenkins_home/workspace/FREESTILE"')
                sh ('find /var/jenkins_home/workspace/FREESTILE/ -name "FreeStyle.zip" ')

                // Upload Artifactory
                 rtUpload (  serverId: JfrogServerID,
                            spec: '''{ "files": [ {
                                            "pattern": "FreeStyle.zip",
                                            "target": "CursoIAC/QA/",
                                            "recursive": "false"
                                    }
                                ]
                            }'''
                        )
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}