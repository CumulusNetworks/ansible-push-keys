
Wait until all of the machines have booted. You can quickly check their status
by running

    for vm in `cat /etc/dhcp/dhcpd.hosts | grep 'host .* {' | cut -d " " -f 2`; do echo "$vm --- " `ping -c 1 $vm | grep transmitted`; done

Run these commands from oob-mgmt-server:

    sudo apt-get install git software-properties-common -y
    sudo apt-add-repository ppa:ansible/ansible -y
    sudo apt-get update
    sudo apt-get install ansible -qy
    git clone https://github.com/cumulusnetworks/ansible-push-keys
    cd ansible-push-keys
    cat /etc/dhcp/dhcpd.hosts | grep 'host .* {' | cut -d " " -f 2 >> hosts
    ansible-playbook push-keys.yml -kK
