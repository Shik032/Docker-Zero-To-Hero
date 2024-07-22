###########################################
# BASE IMAGE
###########################################

FROM ubuntu:20.04 AS build

# Install Python and pip
RUN apt-get update && apt-get install -y python3 python3-pip

# Set the working directory in the container
WORKDIR /app

# Copy the current directory contents into the container at /app
COPY . .


############################################
# HERE STARTS THE MAGIC OF MULTI STAGE BUILD
############################################

FROM gcr.io/distroless/python3-debian10

# Set the working directory in the container
WORKDIR /app

# Copy the necessary files from the build stage
COPY --from=build /app /app

# Command to run the application
CMD ["calculator.py"]
