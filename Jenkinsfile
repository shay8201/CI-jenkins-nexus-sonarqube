pipeline {
    agent any
    tools {
        maven 'MAVEN3'
        jdk 'OracleJDK8'
    }

    environment {
        SNAP-REPO = 'vprofile-snapshot'
        NEXUS-USER = 'admin'
        NEXUS-PASS = 'Aa12345678'
        RELEASE-REPO = 'vprofile-release'
        CENTRAL-REPO = 'vpro-maven-central'
        NEXUS-GRP-REPO = 'vpro-maven-group'
        NEXUSIP = '172.31.16.167'
        NEXUSPORT = '8081'
        NEXUSLOGIN = 'nexuslogin'
    }

    stages {
        stage ('build') {
            steps {
                sh 'mvn -s settings.xml -DskipTests install'
            }
        }
    }
}