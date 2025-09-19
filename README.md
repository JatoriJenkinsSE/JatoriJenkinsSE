## Hi there 👋

<!--
**JatoriJenkinsSE/JatoriJenkinsSE** 


- 🔭 I’m currently working on creating a Rust Microservice Architecture system
- 📫 How to reach me: jatorijenkins@yahoo.com
-->
# Rust Microservice Architecture

Rust Microservice Architecture project

It includes:

* **gateway** – public edge; validates JWT and aggregates downstream calls
* **auth-service** – issues & verifies JWTs
* **user-service** – simple in‑memory user directory
* **common** – shared types, helpers, tracing
* **docker-compose** – one command to boot the whole stack

Built with **Axum 0.7**, **Tokio**, **tower-http**, **jsonwebtoken**, **reqwest**, **tracing**.

---

## GitHub Repository Structure

Create a GitHub repo named:

```
Rust-Microservices-JatoriJenkinsSE
```

Repo Layout:

```
.
├─ Cargo.toml
├─ .env                      # dev env vars
├─ docker-compose.yml
├─ crates/
│  └─ common/
│     └─ src/lib.rs
└─ services/
   ├─ auth-service/
   │  ├─ Cargo.toml
   │  ├─ Dockerfile
   │  └─ src/main.rs
   ├─ user-service/
   │  ├─ Cargo.toml
   │  ├─ Dockerfile
   │  └─ src/main.rs
   └─ gateway/
      ├─ Cargo.toml
      ├─ Dockerfile
      └─ src/main.rs
```

---

## GitHub Personalization

* All files include **JatoriJenkinsSE** as the repository owner.

```bash
git init
git remote add origin https://github.com/JatoriJenkinsSE/Rust-Microservices-JatoriJenkinsSE.git
git add .
git commit -m "Initial commit: Rust microservice architecture"
git push -u origin main
```

---

## GitHub Actions (CI/CD Workflow)

Add `.github/workflows/ci.yml` to automatically test and build when pushing code:

```yaml
name: Rust CI

on:
  push:
    branches: ["main"]
  pull_request:
    branches: ["main"]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v3

      - name: Install Rust
        uses: actions-rs/toolchain@v1
        with:
          toolchain: stable
          override: true

      - name: Build
        run: cargo build --workspace --verbose

      - name: Run Tests
        run: cargo test --workspace --verbose
```

---

## Usage Instructions (GitHub Integrated)

1. Clone the repo:

```bash
git clone https://github.com/JatoriJenkinsSE/Rust-Microservices-JatoriJenkinsSE.git
cd Rust-Microservices-JatoriJenkinsSE
```

2. Run services locally:

```bash
RUST_LOG=info AUTH_SECRET=dev AUTH_SERVICE_PORT=8081 cargo run -p auth-service
RUST_LOG=info USER_SERVICE_PORT=8082 cargo run -p user-service
RUST_LOG=info AUTH_SERVICE_URL=http://localhost:8081 USER_SERVICE_URL=http://localhost:8082 GATEWAY_PORT=8080 cargo run -p gateway
```

3. Run with Docker:

```bash
docker compose up --build
```

4. Push updates to GitHub:

```bash
git add .
git commit -m "Feature update"
git push origin main
```

---
