## Ansible Playbook
  ## Steps
  1. Create required files
      * Vagrantfile 
      ```
      vagrant init geerlingguy/ubuntu2004
      ```
      * hosts -this is our inventory that has the defined servers
      * ansible.cfg -this states our inventory location
      * playbook.yml - this has our main play
      * vars.yml - we define our variables in this file and import them into playbook.yml
  
  2. Vagrant file
     Add the playbook file to the vagrant file
     ```
      config.vm.provision :ansible do |ansible|
            ansible.playbook = "playbook.yml"
        end 
      ```
      Add required ports for the app
  3. Playbook
     1. Use ` vars_files:       - vars.yml ` to include vars file
     2. Use `become: true` to run with priviledges
     3. Define respective roles
       
  4. Initialize roles 
      Make Roles directory then cd into it
      ```
      ansible-galaxy init <roleName>
      ```
      We will use 3 roles in this case and add them to a role folder
      1. git - Installs git
      2. docker -Installs dependencies, docker and docker-compose
      3. docker-compose -Starts our docker compose
      
  7. Run the playbook through vagrant 
      ```
      vagrant up
      ```

>As of 2023-08-01 12:05 pm (deadline) the VM runs but no evidence of docker step completing. 
      
 
  