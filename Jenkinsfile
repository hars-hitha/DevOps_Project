pipeline {
    agent any

    environment {
        REPO = 'https://github.com/hars-hitha/DevOps_Project.git'
<<<<<<< Updated upstream
        QA_HOST = '172.31.36.74'          
        QA_USER = 'sree'
=======
>>>>>>> Stashed changes
        IMAGE = 'myhtmlsite'
        PORT = '8080'
    }

    stages {
<<<<<<< Updated upstream

        stage('Clone Repo') {
            steps {
                git branch: 'main', url: "${REPO}"
=======
        stage('Clone Project') {
            steps {
                git "${REPO}"
>>>>>>> Stashed changes
            }
        }

        stage('Install Docker on QA') {
            steps {
<<<<<<< Updated upstream
                sh """
                ansible all -i '${QA_HOST},' -u ${QA_USER} -m apt -a 'name=docker.io state=present update_cache=yes' --become
                """
=======
                sh 'ansible webservers -m apt -a "name=docker.io state=present update_cache=true" --become'
>>>>>>> Stashed changes
            }
        }

        stage('Copy Project to QA') {
            steps {
<<<<<<< Updated upstream
                sh """
                ansible all -i '${QA_HOST},' -u ${QA_USER} -m synchronize -a 'src=./ dest=/home/${QA_USER}/DevOps_Project delete=yes' --become
                """
=======
                sh 'ansible webservers -m file -a "path=/home/sree/webapp state=directory mode=0755"'
                sh 'ansible webservers -m copy -a "src=. dest=/home/sree/webapp mode=0755"'
>>>>>>> Stashed changes
            }
        }

        stage('Build Docker Image on QA') {
            steps {
<<<<<<< Updated upstream
                sh """
                ansible all -i '${QA_HOST},' -u ${QA_USER} -m shell -a 'cd /home/${QA_USER}/DevOps_Project && docker build -t ${IMAGE} .' --become
                """
=======
                sh 'ansible webservers -a "cd /home/sree/webapp && docker build -t ${IMAGE} ."'
>>>>>>> Stashed changes
            }
        }

        stage('Run Docker Container on QA') {
            steps {
<<<<<<< Updated upstream
                sh """
                ansible all -i '${QA_HOST},' -u ${QA_USER} -m shell -a 'docker rm -f webapp || true && docker run -d --name webapp -p ${PORT}:80 ${IMAGE}' --become
                """
=======
                sh 'ansible webservers -a "docker rm -f webapp || true"'
                sh 'ansible webservers -a "docker run -d -p ${PORT}:80 --name webapp ${IMAGE}"'
>>>>>>> Stashed changes
            }
        }
    }
}
<<<<<<< Updated upstream

=======
>>>>>>> Stashed changes
