node {
    stage('Preparation'){
        sh 'git checkout scm'
    }
    stage('Maven build'){
        sh 'docker run -i -v $PWD:/usr/src/mymaven -w /usr/src/mymaven --rm maven:3-jdk-8 mvn clean install'
    }
    stage('Results'){
        junit '**/target/surefire-reports/TEST-*.xml'
        archiveArtifacts 'target/gildedrose-*.jar'
    }
    stage('javadoc'){
        sh 'docker run -i -v $PWD:/usr/src/mymaven -w /usr/src/mymaven --rm maven:3-jdk-8 mvn javadoc:javadoc'
    }
}