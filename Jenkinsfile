pipeline {
    agent {
        label "ansible_docker"
    }

    stage("Git checkout"){
        git  'git@github.com:Alexdev87/example-playbook-1.git'
    }
    stage("Check ssh key"){
        secret_check=true
    }
    stage("Run playbook"){
        if (secret_check){
            sh 'ansible-galaxy install -r requirements.yml'
            sh 'ansible-playbook -i inventory/prod.yml site.yml'
        }
        else{
            echo 'no more keys'
        }
        
    }
}
