# Certification_task
1. Установить jenkins на хост машину.
2. установить плагины Terraform и Ansible 
3. Добавить в jenkins credentions as secret text:
 - AWS_ACCESS_KEY_ID
 - AWS_SECRET_ACCESS_KEY
4. Добавить в jenkins credentions as SSH Username with private key:
 - username - ubuntu
 - private key - Enter directly из файла id_rsa
5. Создать Piplene job из файла Jenkins
6. Запустить

PS можно и в контейнере:
    docker run -d -u 2000 -p 8080:8080 -p 50000:50000 -v /tmp:/var/jenkins_home marcelmaatkamp/jenkins-docker-gitlab-ansible:latest
