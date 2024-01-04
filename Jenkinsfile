pipeline {
agent {
label 'buildserver'
}

stages {

stage ('Checkout') 
{
steps
    {
    
        checkout scm
        
    }
    
}
stage ('Build') 
{
    steps
    {
       sh "cd /home/ubuntu/workspace/Java-job-deplyment/account-service ; mvn clean install " 
    }
}

   
stage ('dockerimageBuild')
    {
    steps
    {
        sh "cd /home/ubuntu/workspace/Java-job-deplyment/account-service; sudo docker build -t account-service . " 
    }
}
     stage ('dockerimagepush ') 
{
    steps
    {
       sh "cd /home/ubuntu/workspace/Java-job-deplyment/account-service ; sudo  docker login anusha167 neversay100# "
        sh "cd /home/ubuntu/workspace/Java-job-deplyment/account-service ; sudo docker tag account-service anusha167/account-service "
        sh "cd /home/ubuntu/workspace/Java-job-deplyment/account-service ; sudo docker push anusha167/account-service  "
        
        
    }
}
 stage ('Deploying as a container')
    {
        steps ('deploying'){
            sh "sudo docker run -d --name c1 -p 2222:2222 account-service "
         
        }
        
    }  
   
//stage ('k8sdeployment') 
 //  {
 //     steps {
   //        node (' ansible') {
    //        sh " sudo ansible-playbook /etc/ansible/k8s.yaml"
   
    //}
//}
//}
}
    
 
}
