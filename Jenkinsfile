node("agent-01"){
    stage("Git checkout"){
        git branch: 'main', credentialsId: 'f2247888-7db8-497e-9cc3-cc787ea4d74d', url: 'git@github.com:rdegtyarev/mnt-08-04.git'
    }
    stage("Sample define secret_check"){
        secret_check=true
    }
    stage("Run playbook"){
        if (secret_check){
            inputMap = input message: 'Введите ip адреса серверов', parameters: [
                string(name: 'ELASTIC_IP', trim: true), 
                string(name: 'KIBANA_IP', trim: true),
                string(name: 'APP_IP', trim: true),
                ]
            ansiblePlaybook disableHostKeyChecking: true, credentialsId: '58904c8d-9144-4285-ad1a-6d47490964bd', extras: "-e ELASTIC_IP=${inputMap['ELASTIC_IP']} -e KIBANA_IP=${inputMap['KIBANA_IP']} -e APP_IP=${inputMap['APP_IP']}", inventory: 'inventory/elk/', playbook: 'site.yml'
        }
        else{
            echo 'need more action'
        }
    }
}
