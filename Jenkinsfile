  node{
      stage('Clone') {
          checkout scm
      }
      stage('Creation ssh'){

          '''
          apk add sshpass
          ssh-keygen -q -t rsa -N \'\' -f /root/.ssh/id_rsa
          sshpass -p \'lab2022\' ssh-copy-id  -o stricthostkeychecking=no root@app-salaire.alexis.form
          '''
      }
      stage('Ansible') {
        ansiblePlaybook (
            colorized: true,          
            playbook: 'playbook.yml',
            inventory: 'hosts.yml'
        )
      }
  }
