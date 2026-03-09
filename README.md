# docker-caching-mechanism
This repository demonstrates the basic Docker workflow and helps understand how Docker layer caching works when building images.

---
### Agenda
- Writing a basic Dockerfile
- Building a Docker Image
- Running a Docker Container
- Understanding Docker Layers
- Observing Docker Build Cache Mechanism
- How modifying Dockerfile instructions affects image rebuilding

---
### Prerequisites
- Basic knowledge of Docker
- Docker installed on your system
- Basic command line knowledge
- MobaXterm Tool
---

#### 1.Accessing the Remote Server Using MobaXterm and Instance Public IP
<img width="1919" height="1010" alt="Screenshot 2026-03-09 143142" src="https://github.com/user-attachments/assets/c52ab57f-6820-4b01-afbf-b8df82b33a1e" />

#### 2.Create and Navigate to Project Directory
<img width="1919" height="1008" alt="Screenshot 2026-03-09 143242" src="https://github.com/user-attachments/assets/d92df519-c91c-4729-9187-1d530110fee8" />

#### 3.Write app.py vim app.py
<img width="1919" height="1004" alt="Screenshot 2026-03-09 143429" src="https://github.com/user-attachments/assets/0b460d23-fa53-4bb9-a29c-20d5134010b1" />

#### 4.Write Dockerfile vim Dockerfile
<img width="1919" height="1000" alt="Screenshot 2026-03-09 143616" src="https://github.com/user-attachments/assets/c0686b48-573c-4cf8-b6bd-4420de3a2bb9" />

- FROM python : Specifies the base image for the Docker image.Docker pulls the official Python image from Docker Hub if it is not available locally.All subsequent instructions run on top of this base image.Ensures the container already has Python installed to run the application.

- WORKDIR /app : Sets the working directory inside the container.If the /app directory does not exist, Docker creates it automatically.
All following instructions (COPY, RUN, CMD) will execute inside this directory.

- COPY app.py . : Copies files from the host machine to the container filesystem.app.py is copied from the current directory of the host system. . means the file will be placed in the current working directory inside the container (/app).

CMD ["python", "app.py"] :Defines the default command that runs when the container starts.It runs the Python script app.py When the container starts, Docker executes:python app.py A Dockerfile can have only one CMD instruction. If multiple CMD instructions are written, only the last one will be executed and previous ones will be ignored.

#### 5.Before building container make sure both file has been created app.py and Dockerfile
<img width="1919" height="1006" alt="Screenshot 2026-03-09 143625" src="https://github.com/user-attachments/assets/c1920335-17e4-46d9-aaf7-dbd044c0aa75" />

#### 6.Built first-python-app image using dockerfile 
<img width="1919" height="997" alt="Screenshot 2026-03-09 143854" src="https://github.com/user-attachments/assets/577085f0-5cb7-43c8-9fc0-071791379057" />

<img width="1482" height="223" alt="image" src="https://github.com/user-attachments/assets/d7cb5bf6-9dd5-46c9-ac91-279ad3895a16" />

#### 7.Create container and run container using container id
<img width="1919" height="1003" alt="Screenshot 2026-03-09 144313" src="https://github.com/user-attachments/assets/4729d412-5e35-4fb9-bcf2-bb9353adf67d" />

#### 8.Modified existing docker file 
<img width="1919" height="1016" alt="Screenshot 2026-03-09 192745" src="https://github.com/user-attachments/assets/127c415b-e8fc-4d1e-be39-092d70cc5d17" />

#### 9.Built second-python-app image using modified dockerfile
<img width="1919" height="1001" alt="Screenshot 2026-03-09 145322" src="https://github.com/user-attachments/assets/a209bca0-e548-4a06-9632-4719f0fe6ed8" />

- Docker uses a layer caching mechanism to speed up the image build process.
- When building an image, Docker checks each instruction in the Dockerfile from top to bottom.
- If an instruction has not changed and its context (files used in that instruction) also has not changed, Docker reuses the previously built layer from cache.
- In the build output we observed:
CACHED [2/4] WORKDIR /app
CACHED [3/4] COPY app.py .
This means Docker did not rebuild these layers and instead reused them from the previous build.

#### 10.Create container and run container using container id
<img width="1919" height="1006" alt="Screenshot 2026-03-09 145514" src="https://github.com/user-attachments/assets/f562a85b-0dcf-44bc-aa75-ed9d41494de5" />









