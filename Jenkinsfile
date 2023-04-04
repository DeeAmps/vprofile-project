pipeline {
    tools {
        jdk 'jdk8'
        maven 'maven'
    }
    agent any

    environment {
        SNAP_REPO = "vprofile-snapshot"
        NEXUS_CREDS = credentials('nexuslogin')
        NEXUS_USER = "${NEXUS_CREDS_USR}"
        NEXUS_PASS = "${NEXUS_CREDS_PSW}"
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
            post {
                success {
                    echo "Now Achiving"
                    archiveArtifacts artifacts: '**/*.war'
                }
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Checkstyle Analysis') {
            steps {
                sh 'mvn checkstyle:checkstyle'
            }
        }
    }
}