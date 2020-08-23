# Init docker containers as remote hosts

1. Start docker containers, they will be used as remote hosts
    
    `sudo docker-compose up -d`

1. Check ssh connection (optional, password - *ansible*)
    
    `ssh root@localhost -p 5020`

1. Copy local ssh keys to containers

    `ssh-copy-id -i ~/.ssh/id_rsa.pub root@localhost -p 5020`
    
    `ssh-copy-id -i ~/.ssh/id_rsa.pub root@localhost -p 5021`

1. Install python in containers (optional, if needed)

    `ansible -i my-inventory.ini all -m raw -a "apt-get install -y python"`
    
1. Ping hosts

    `ansible -i my-inventory.ini docker -m ping`

# Mongodb

1. `ansible-playbook -i my-inventory.ini mongodb/site.yaml`

# TODO
1. Install latest mongodb version
1. Set mongodb cluster