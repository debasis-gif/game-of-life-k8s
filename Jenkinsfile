node {
    stage('scm'){
        git 'https://github.com/singaravellu/game-of-life.git'
    }
    stage('build'){
        sh 'mvn package'
    }
    stage('archiving artifactes')
    {
        sh 'whoami'
        archiveArtifacts 'gameoflife-web/target/*.war'
    }
    stage ('building docker image')
    {
        echo "building the docker image  "
        sh 'docker image build -t dockersing/gameoflife:1.0 .'
    }
    stage('Push the docker image to hub'){
        withCredentials([usernamePassword(credentialsId: 'DockerCred', passwordVariable: 'passwd', usernameVariable: 'username')]) {
         sh 'docker login -u ${username} -p{passwd} '   
    // some block
      }
      sh 'docker push dockersing/gameoflife:1.0'
    }
}