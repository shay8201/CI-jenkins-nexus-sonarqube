pipeline {
    agent any
    tools {
        maven 'MAVEN3'
        jdk 'OracleJDK8'
    }

    environment {
        SNAP_REPO = 'vprofile-snapshot'
        NEXUS_USER = 'admin'
        NEXUS_PASS = 'Aa12345678'
        RELEASE_REPO = 'vprofile-release'
        CENTRAL_REPO = 'vpro-maven-central'
        NEXUS_GRP_REPO = 'vpro-maven-group'
        NEXUSIP = '172.31.16.167'
        NEXUSPORT = '8081'
        NEXUSLOGIN = 'nexuslogin'
    }

    stages {
        stage ('build') {
            steps {
                sh 'mvn -s settings.xml -DskipTests install'
            }
            post {
                success {
                    echo 'Now Archiving'
                    archiveArtifacts artifacts: '**/*.war'
                }
            }
        }

        stage ('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage ('') {
            steps {
                sh 'mvn checkstyle:checkstyle'
            }
        }
    }
}