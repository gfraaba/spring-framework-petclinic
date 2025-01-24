**NOTE: "mcr.microsoft.com/devcontainers/universal" is not available for ARM64!**
*https://github.com/Azure-Samples/azure-container-apps-java-samples/tree/main/spring-petclinic*

brew install gh
gh --version
gh repo fork spring-petclinic/spring-framework-petclinic
cd cd ./spring-framework-petclinic/ && gh repo set-default gfraaba/spring-framework-petclinic
git remote -v
git merge upstream/main
git push origin main

https://mcr.microsoft.com/en-us/artifact/mar/devcontainers/universal/about
# docker pull mcr.microsoft.com/devcontainers/universal:2   
- 2: Pulling from devcontainers/universal
- no matching manifest for ***linux/arm64/v8*** in the manifest list entries

# As of 2025.01.24, only 2 tags seem to work (and why? no idea!)! 2.1-focal and 2.2.0-focal 

## Build and Open in Container: This requires 12+ GB! Inside Dev Container's VS Code Terminal, run the following command to start the application:
- *NOTE: The VS Code terminal title says "rosetta"
- Run: dpkg --print-architecture 
- Displays amd64!! (In Docker Desktop > Containers: you see 'AMD64' and a warning (when you hover your mouse on that) that says: Image may have poor performance, or fail, if run via emulation)
- Now run: ./mvnw jetty:run-war