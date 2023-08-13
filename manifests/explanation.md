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
      * mongodb-statefulset.yaml -Stateful set for mongo db
      * client-deployment.yaml - describes  our deployment nodes for `mattwanjau/yolo-client:V2.0.0` container(s)
      * client-service.yml - specifies a port to access the client
      * client-deployment.yaml - describes  our deployment for `mattwanjau/yolo-client:V2.0.0` container(s)
      * backend-service.yaml - describes

  3. Use kubectl to apply files 
     * Apply mongodb-service.yaml
        ```
        kubectl apply -f manifests/mongodb-service.yaml
        ```
        run `kubectl get svc` to verifyservice mongo db has been created
     * Apply mongodb-statefulset.yaml to create stateful pod (single).
        ```
        kubectl apply -f manifests/mongodb-statefulset.yaml
        ```
       run   `kubctl get pv` to verify existence of persistene volume
     *  

       
      