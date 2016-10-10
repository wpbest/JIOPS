# We use the microsoft/dotnet image as a starting point.
FROM microsoft/dotnet:latest

# Install build essentials, nodjs and git
RUN apt-get update
RUN apt-get install -y build-essential nodejs nodejs-legacy git

# Create a folder to clone our source code
RUN mkdir repositories

# Set our working folder
WORKDIR repositories

# Clone the source code 
RUN git clone https://github.com/wpbest/JIOSP.git

# Set our working folder 
WORKDIR jiops/src/dotnetstartercd ji	

COPY project.json .
RUN ["dotnet", "restore"]

COPY . /app
RUN ["dotnet", "build"]

EXPOSE 5000/tcp

ENTRYPOINT ["dotnet", "run", "--server.urls", "http://0.0.0.0:5000"]
