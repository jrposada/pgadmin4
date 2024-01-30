1. First time setup.

   1. Create new builder for multi platform building:

   ```
   docker buildx create --name raspberry-builder --bootstrap --use
   ```

   After running above command `docker buildx ls` should look something like this:

   ```
   $ docker buildx ls
   NAME/NODE            DRIVER/ENDPOINT             STATUS  BUILDKIT             PLATFORMS
   raspberry-builder *  docker-container
       raspberry-builder0 unix:///var/run/docker.sock running v0.12.4              linux/amd64, linux/amd64/v2, linux/amd64/v3, linux/arm64, linux/riscv64, linux/ppc64le, linux/s390x, linux/386, linux/mips64le, linux/mips64, linux/arm/v7, linux/arm/v6
   default              docker
       default            default                     running v0.12.4+3b6880d2a00f linux/amd64, linux/amd64/v2, linux/amd64/v3, linux/arm64, linux/riscv64, linux/ppc64le, linux/s390x, linux/386, linux/mips64le, linux/mips64, linux/arm/v7, linux/arm/v6
   ```


1. Build multi platform image
   ```
   docker buildx build --platform linux/amd64,linux/arm64,linux/arm/v7 -t jrposada/pgadmin4:latest --push .
   ```
