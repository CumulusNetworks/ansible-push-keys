sudo apt-get install git software-properties-common -y
sudo apt-add-repository ppa:ansible/ansible -y
sudo apt-get update
sudo apt-get install ansible -qy
git clone https://github.com/cumulusnetworks/ansible-push-keys
cd ansible-push-keys
ansible-playbook push-keys.yml -kK
