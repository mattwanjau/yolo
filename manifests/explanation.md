## K8s Deployment
  ## Steps
  1. Create manifests folder
  2. Built existiong Dockerfile containers (front end and backend) and pushed to dockerhub
      
      ```
      docker build -t mattwanjau/yolo-backend:v2.0.0 backend/
      docker push mattwanjau-yolo-backend:v2.0.0
      ```
  2. Create manifests files

      * mongodb-service.yaml - to create the headless mongo db service
      * ansible.cfg -this states our inventory location
      * playbook.yml - this has our main play
      * vars.yml - we define our variables in this file and import them into playbook.yml

  3. Apply mongodb-service.yaml
  
     Add the playbook file to the vagrant file
     ```
      config.vm.provision :ansible do |ansible|
            ansible.playbook = "playbook.yml"
        end 
      ```