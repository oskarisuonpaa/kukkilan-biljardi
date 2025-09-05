# Kukkilan Biljardi

This repository contains code for Kukkilan Biljardi's web application.

## Requirements

- Rust
- Node
- Git

## Getting Started

1. To get started, you first need to clone the repository.
2. Next you need to get the submodules: //TODO insert command here
3. To setup frontend, you need to download depedencies by running the following command inside the frontend subfolder: `npm install`.
4. Then using separate terminal instance, navigate to the backend subfolder and run the following command to start the backend: `cargo run`.
5. Finally start the frontend by running the following command inside the frontend subfolder: `npm run dev` (NOTE: This is development mode which shouldn't be used to deploy the app).

## Repository Content

### Frontend

Frontend is included as a submodule in `./frontend/` which contains the frontend of the application which uses NextJs 15.

### Backend

Backend is included as as submodule in `./backend/` which contains the backend of the application which is written in rust.

### Workflows (CI/CD)

Frontend and backend both have their own continuous integration (CI) workflows and this repository contains continuos delivery (CD) workflows. The workflows can be found within root of each repository (`./github/workflows/`).
