node('master'){
    stage("Clean workspace"){
        cleanWs()
    }
    stage("Clone Repo"){
        git branch: 'main', url: 'https://github.com/chinastockproducts/Iac-eks.git'
    }
    stage("Create EKS cluster"){
        sh """
           source /var/jenkins_home/aws_credentials
           terraform init
           terraform plan
           terraform apply --auto-approve
           cp kubeconfig_eks-cluster /var/jenkins_home/kubeconfig
 
        """
    }
}
