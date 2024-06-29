# Info
- A small project for understanding how can i live code with quarkus..
- In resources we change the application.properties to open the port for the live coding
- We will simply create a pod that exposes those ports out for us in the exterior
  - For this we will create a image that has java 17 installed to run our jar that will be mapped here
  - The config is in the kubernetes image
  - Remmeber that we builded the quarkus app using `mvn package`, so we just need to run the java app inside of target/quarkus-app/quarkus-run.jar
- We must pass a env variable like: 
  ```
  - name: QUARKUS_LAUNCH_DEVMODE 
    value: "true"
  ```
- After everything just use `mvn quarkus:remote-dev`
- After that we can test it using:
  ```
    grpcurl -plaintext -d '{"name": "Alice"}' 172.24.166.62:30001 hello.HelloGrpc/SayHello
  ```