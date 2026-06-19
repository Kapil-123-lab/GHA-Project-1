# ☕ Java CI/CD Pipeline with GitHub Actions

![GitHub Actions](https://img.shields.io/badge/CI%2FCD-GitHub_Actions-2088FF?style=flat-square&logo=githubactions)
![Java](https://img.shields.io/badge/Language-Java-ED8B00?style=flat-square&logo=openjdk)
![Maven](https://img.shields.io/badge/Build-Maven-C71A36?style=flat-square&logo=apachemaven)
![Docker](https://img.shields.io/badge/Container-Docker-2496ED?style=flat-square&logo=docker)

---

## 📌 Project Overview

This project demonstrates a **CI/CD pipeline for a Java Spring Boot application** using **GitHub Actions**.  
It automates the full software delivery process — from code push to Docker image published on DockerHub — without any external CI server like Jenkins.

Built to validate the **GitHub Actions** skill in a real pipeline context using an enterprise-standard Java stack.

---

## 🔧 Tech Stack

| Tool | Purpose |
|------|---------|
| **GitHub Actions** | CI/CD pipeline — workflow triggered on push/PR |
| **Java (Spring Boot)** | Application framework |
| **Maven** | Build tool — compile, test, package |
| **Docker** | Containerize the built JAR |
| **DockerHub** | Container image registry |

---

## 🔄 Pipeline Workflow

```
Code Push / Pull Request
        │
        ▼
GitHub Actions Triggered (.github/workflows/)
        │
   ┌────▼────┐
   │  Build  │  mvn compile
   └────┬────┘
        │
   ┌────▼────┐
   │  Test   │  mvn test
   └────┬────┘
        │
   ┌────▼──────────┐
   │  Package      │  mvn package → .jar
   └────┬──────────┘
        │
   ┌────▼──────────┐
   │  Docker Build │  Build image from Dockerfile
   └────┬──────────┘
        │
   ┌────▼──────────┐
   │  Docker Push  │  Push to DockerHub registry
   └───────────────┘
```

---

## 📂 Repository Structure

```
GHA-Project-1/
│
├── .github/
│   └── workflows/
│       └── ci.yml               # GitHub Actions pipeline definition
│
├── src/
│   └── main/java/com/example/   # Java Spring Boot application source
│
├── Dockerfile                   # Container image build instructions
└── pom.xml                      # Maven project configuration & dependencies
```

---

## ⚙️ GitHub Actions Workflow Highlights

- **Trigger:** Runs on every `push` and `pull_request` to `main`
- **Build:** `mvn compile` to verify the code compiles cleanly
- **Test:** `mvn test` runs unit tests; pipeline fails if any test fails
- **Package:** `mvn package` produces the executable `.jar`
- **Docker:** Multi-stage aware build; image tagged with commit SHA for traceability
- **Registry:** Pushes to DockerHub using repository secrets (no hardcoded credentials)

---

## 🔐 Secrets Configuration

Credentials are stored as **GitHub Repository Secrets** — never hardcoded:

| Secret Name | Purpose |
|-------------|---------|
| `DOCKERHUB_USERNAME` | DockerHub login |
| `DOCKERHUB_TOKEN` | DockerHub access token (not password) |

To configure: **Repo Settings → Secrets and variables → Actions → New repository secret**

---

## 💡 Why GitHub Actions over Jenkins?

| | GitHub Actions | Jenkins |
|---|---|---|
| Setup | Zero — built into GitHub | Requires server setup |
| Configuration | YAML in repo | Jenkinsfile + plugins |
| Cost | Free for public repos | Server hosting cost |
| Best for | Open source / GitHub-native | Enterprise / complex pipelines |

This project uses GitHub Actions to demonstrate cloud-native CI/CD without infrastructure overhead.

---

## 📚 Key Learnings

- Writing GitHub Actions workflow YAML from scratch
- Maven build lifecycle — compile → test → package
- Docker image build and push within a CI workflow
- GitHub Secrets for secure credential management
- Difference between Jenkins-based and GitHub Actions-based CI/CD

---

## 🔮 Future Improvements

- Add SonarQube code quality analysis step
- Add Trivy image vulnerability scanning before push
- Deploy to AWS ECS/EKS as CD stage
- Add PR-only vs main-branch conditional steps

---

## 👤 Author

**Kapil Kanaujiya** — DevOps Engineer | 4 years BFSI Production Support  
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=flat-square&logo=linkedin)](https://linkedin.com/in/kapil-kanaujiya-4331191a1)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=flat-square&logo=github)](https://github.com/Kapil-123-lab)
