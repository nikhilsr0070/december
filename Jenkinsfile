#job1

pipeline {
  agent any
  stages {
    stage('1st job') {
      steps {
          sshPublisher(publishers: [sshPublisherDesc(configName: 'dev', transfers: [sshTransfer(execCommand:'echo $PWD')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
        sh 'echo "1st job"'
      }
    }

  }
  parameters {
    string(name: 'string1stparam', defaultValue: '', description: '')
    choice(name: 'choicepara', choices: [], description: '')
  }
}


#job2

    pipeline {
  agent any
  stages {
    stage('2nd job') {
      steps {
          sshPublisher(publishers: [sshPublisherDesc(configName: 'makedev', transfers: [sshTransfer(execCommand:'echo $PWD')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
        sh 'echo "2nd job"'
      }
    }

  }
  parameters {
    string(name: 'stringparam', defaultValue: '', description: '')
  }
  triggers {
    upstream(upstreamProjects: 'vjob1, ', threshold: hudson.model.Result.SUCCESS)
  }
}


#job3

pipeline {
  agent any
  stages {
    stage('3rd job') {
        
      steps {
          sshPublisher(publishers: [sshPublisherDesc(configName: 'prod', transfers: [sshTransfer(execCommand:'echo $BASH')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
        sh 'echo "3rdnd job"'
      }
    }

  }
  parameters {
    string(name: 'stringparam', defaultValue: '', description: '')
    choice(name: 'choicepara', choices: [], description: '')
  }
  triggers {
    upstream(upstreamProjects: 'vjob2, ', threshold: hudson.model.Result.SUCCESS)
  }
}
