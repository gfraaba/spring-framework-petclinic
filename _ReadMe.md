**NOTE: "mcr.microsoft.com/devcontainers/universal" is not available for ARM64!**
*https://github.com/Azure-Samples/azure-container-apps-java-samples/tree/main/spring-petclinic*

## Using GitHub CLI to Fork a Repository

To fork a repository using the GitHub CLI, follow these steps:

1. **Install GitHub CLI**:
   ```sh
   brew install gh

   gh --version
   ```

2. **Authenticate with GitHub**:
   ```sh
   gh auth login
   ```

3. **Fork the Repository**:
   ```sh
   gh repo fork spring-petclinic/spring-framework-petclinic
   ```

## Keeping Your Forked Repository Up-to-Date

To keep your forked repository up-to-date with the original repository, follow these steps:

1. **Add the original repository as a remote**:
   ```sh
   git remote add upstream https://github.com/spring-petclinic/spring-framework-petclinic.git
   ```

2. **Ensure the `origin` is set to your forked repository**:
   ```sh
   git remote set-url origin https://github.com/gfraaba/spring-framework-petclinic.git
   ```
   > Note: This command accomplishes the same as `gh repo set-default gfraaba/spring-framework-petclinic`. You can use either command to set the default repository.

3. **Fetch the latest changes from the original repository**:
   ```sh
   git fetch upstream
   ```

4. **Merge the changes into your fork's main branch**:
   ```sh
   git checkout main
   git merge upstream/main
   ```

5. **Push the updated main branch to your fork on GitHub**:
   ```sh
   git push origin main
   ```

## Confirming Your Remote URLs

To confirm that your local repository is pointing to your newly forked repository:

1. **Check the Current Remote URL**:
   ```sh
   git remote -v
   ```

## Comparing Your Forked Repository with Upstream

To compare your forked repository with the upstream repository:

1. **Fetch the latest changes from the upstream repository**:
   ```sh
   git fetch upstream
   ```

2. **Compare your forked repository with the upstream repository**:
   ```sh
   git diff upstream/main
   ```

3. **See a summary of the differences**:
   ```sh
   git diff --stat upstream/main
   ```
```


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