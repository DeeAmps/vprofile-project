pipeline {
    tools {
        jdk 'jdk8'
        maven 'maven'
    }
    agent any

    environment {
        SNAP_REPO = "vprofile-snapshot"
        NEXUS_CREDS = credentials('nexuslogin')
        NEXUS_USER = "${NEXUS_CREDS_USERNAME}"
        NEXUS_PASS = "${NEXUS_CREDS_PASSWORD}"
        RELEASE_REPO = "vprofile-release"
        CENTRAL_REPO = "vprofile-maven-central"
        NEXUSIP = "54.224.162.51"
        NEXUSPORT = "8081"
        NEXUS_LOGIN = "nexuslogin"
        NEXUS_GRP_REPO = "vprofile-group"
    }

    stages {
        stage('Build') {
            steps {
                sh 'mvn -s settings.xml -DskipTests install'
            }
        }
    }
}