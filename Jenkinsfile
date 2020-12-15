
timestamps {

node () {

	stage ('first job - Build') {
 	
sshPublisher(publishers: [sshPublisherDesc(configName: 'Dev', transfers: [], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
sh """ 
df -h
ls 
 """ 
	}
	stage ('second job - Build') {
 	
sshPublisher(publishers: [sshPublisherDesc(configName: 'nikhil-user', transfers: [], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
sh """ 
ls -altr
cat /etc/*release 
 """ 
	}
	stage ('third job - Build') {
 	
sshPublisher(publishers: [sshPublisherDesc(configName: 'Deploy-test', transfers: [], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
sh """ 
echo "----this is success job" 
 """ 
	}
}
}
