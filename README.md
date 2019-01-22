# Linux-configuration:
# server Info:
    - IP address: 18.197.254.118
    - SSH port : 2200
    - host : http://18.197.254.118

# Installed Software:
     apache2
     libapache2-mod-wsgi
     flask
     flask-sqlalchemy
     requests
     sqlalchemy
     httplib2
     oauthlib
     oauth2client
     finger

# Steps of Config:
  - chmod 600 instance_key
  - ssh -i instance_key ubuntu@public_ip
  - sudo su -
  - sudo adduser grader
  - sudo nano /etc/sudoers.d/grader
     then add grader ALL=(ALL:ALL)
  - sudo apt-get update
  - sudo apt-get upgrade
  - sudo apt-get install finger
  - ssh-keygen -f ~/.ssh/udacity.rsa
  - cat ~/.ssh/udacity.rsa.pub
  - cd /home/grader
  - mkdir .ssh
  - touch .ssh/authorized_keys
  - nano .ssh/authorized_keys --> then past the public key
  - sudo chmod 700 /home/grader/.ssh
  - sudo chmod 644 /home/grader/.ssh/authorized_keys
  - sudo chown -R grader:grader /home/grader/.ssh
  - sudo service ssh restart
  - sudo nano /etc/ssh/sshd_config
    [PasswordAuthentication: no][df1]
    [Port 22][df1] to [Port 2200][df1]
    [PermitRootLogin: no][df1]
  - sudo service ssh restart
  - sudo ufw allow 2200/tcp
  -  sudo ufw allow 80/tcp 
  - sudo ufw allow 123/udp
  - sudo ufw enable
  #  Ubuntu terminal and built-in ssh
