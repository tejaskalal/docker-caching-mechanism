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

#### 3.Write app.py ```bash
vim app.py
<img width="1919" height="1004" alt="Screenshot 2026-03-09 143429" src="https://github.com/user-attachments/assets/0b460d23-fa53-4bb9-a29c-20d5134010b1" />



