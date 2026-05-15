pipeline {
    agent any

    environment {
        KUBECONFIG = '/var/lib/jenkins/.kube/config'
    }

    stages {

        stage('Run Ansible Kubernetes Playbook') {
            steps {
                sh '''
                ansible-playbook \
                -i /home/innuser009/ansible-lab/inventory \
                /home/innuser009/ansible-lab/nginx-k8s.yml
                '''
            }
        }

        stage('Verify Kubernetes Deployment') {
            steps {
                sh 'kubectl get pods -n ansible-demo'
                sh 'kubectl get svc -n ansible-demo'
            }
        }
    }
}
