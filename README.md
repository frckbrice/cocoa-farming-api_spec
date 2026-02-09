# CocoaFlow API Specification

[![OpenAPI 3.1.0](https://img.shields.io/badge/OpenAPI-3.1.0-green.svg)](https://spec.openapis.org/oas/v3.1.0)
[![License: Apache 2.0](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![Node.js](https://img.shields.io/badge/Node.js-22+-green.svg)](https://nodejs.org/)
[![Redocly](https://img.shields.io/badge/Redocly-Latest-orange.svg)](https://redocly.com/)
[![CI/CD](https://img.shields.io/badge/CI/CD-GitHub%20Actions-blue.svg)](https://github.com/features/actions)
[![Docker](https://img.shields.io/badge/Docker-Containerized-blue.svg)](https://www.docker.com/)
[![TypeScript](https://img.shields.io/badge/TypeScript-Client%20Generated-blue.svg)](https://www.typescriptlang.org/)

Professional OpenAPI 3.1.0 specification for CocoaFlow, a cocoa industry management platform. The repository provides the API contract, interactive documentation, and generated artifacts (TypeScript client and Postman collection) with CI/CD and containerized deployment.

## Overview

CocoaFlow API defines a production-ready contract for cocoa industry operations: farmer and farm management, GPS and inspection data, Rainforest Alliance certification, campaigns, markets, transactions, training, and subscriptions. The spec is the single source of truth for frontend and backend integration.

### Technical Highlights

- **OpenAPI 3.1.0** with modular paths and reusable components
- **50+ endpoints** across auth, users, companies, farms, projects, campaigns, markets, transactions, training, inspections, audits, and subscriptions
- **Standardized request/response examples** and error schemas (4xx/5xx)
- **JWT Bearer and API key** security; rate limiting and validation
- **Generated TypeScript client** (OpenAPI Generator) and **Postman collection** for testing
- **CI/CD** (GitHub Actions), **Docker** image for docs, and deployment to GitHub Pages / Vercel

## Quick Start

### Prerequisites

- Node.js 22+
- npm 8+
- Docker (optional)

### Installation

```bash
git clone git@github.com:frckbrice/project-api_spec.git
cd project-api_spec
npm install
npm run docs:serve
```

Documentation is served at `http://localhost:8080`.

### Scripts

| Command                    | Description                                           |
| -------------------------- | ----------------------------------------------------- |
| `npm run docs:serve`       | Serve interactive docs (port 8080)                    |
| `npm run docs:build`       | Build static documentation                            |
| `npm run bundle`           | Bundle spec to `dist/cocoaflow-api.yaml`              |
| `npm run lint`             | Lint OpenAPI spec                                     |
| `npm run validate`         | Validate against OpenAPI 3.1.0                        |
| `npm run test`             | Lint, validate, format check                          |
| `npm run generate:client`  | Generate TypeScript client to `generated/typescript/` |
| `npm run generate:postman` | Generate Postman collection to `generated/postman/`   |

### Docker

```bash
docker build -t cocoaflow-api-docs .
docker run -p 8080:8080 cocoaflow-api-docs
```

## Documentation and Deployment

| Environment  | URL                                                                                   | Notes                      |
| ------------ | ------------------------------------------------------------------------------------- | -------------------------- |
| GitHub Pages | [project-api_spec](https://frckbrice.github.io/project-api_spec)                      | Published docs             |
| Raw spec     | [cocoaflow-api.yaml](https://frckbrice.github.io/project-api_spec/cocoaflow-api.yaml) | Bundled OpenAPI YAML       |
| Local        | `http://localhost:8080`                                                               | After `npm run docs:serve` |

## Project Structure

```
project-api_spec/
├── swt_api_spec/                 # OpenAPI source
│   ├── components/
│   │   ├── schemas/              # Data models
│   │   ├── responses/            # Reusable response definitions
│   │   └── parameters/           # Shared parameters
│   ├── paths/                    # Endpoints by domain (auth, user, companies, farm, project, etc.)
│   └── cocoaflow-api.yaml       # Root spec
├── dist/                         # Bundled spec (output of bundle)
├── generated/                    # Generated artifacts (gitignored; run generate scripts to create)
│   ├── typescript/               # Generated TypeScript client (npm run generate:client)
│   └── postman/                  # Generated Postman collection (npm run generate:postman)
├── postman/                      # Legacy/unused; Postman output lives in generated/postman/
├── public/                       # Built documentation assets
├── .github/workflows/            # CI/CD
├── redocly.yaml                  # Redocly and lint config
├── Dockerfile                    # Docs server image
└── package.json
```

## Adding or Changing Endpoints

1. Add or edit YAML under `swt_api_spec/paths/` (and `components/schemas/` if needed).
2. Reference new paths in `swt_api_spec/cocoaflow-api.yaml` under `paths:`.
3. Include request body examples for POST/PUT/PATCH and response examples for success and errors.
4. Run `npm run lint && npm run validate`, then `npm run docs:serve` to verify.

## Security and Compliance

- **Auth**: JWT Bearer (primary), API key for service-to-service, OAuth2 optional.
- **Practices**: HTTPS, rate limiting, input validation, CORS, security headers.
- **Compliance**: Rainforest Alliance-related flows, audit considerations, data privacy.

## Generated Artifacts

- **TypeScript client**: `npm run generate:client` (requires `npm run bundle` first). Output in `generated/typescript/`.
- **Postman collection**: `npm run generate:postman`. Output in `generated/postman/`.
- **Interactive API Documentation**: [https://project-apispec.vercel.app](https://project-apispec.vercel.app)
- **Raw OpenAPI Specification**: [https://project-apispec.vercel.app/cocoaflow-api.yaml](public/cocoaflow-api.yaml)
- **GitHub Repository**: [https://github.com/frckbrice/project-api_spec](https://github.com/frckbrice/project-api_spec)
- **Issue Tracking**: [https://github.com/frckbrice/project-api_spec/issues](https://github.com/frckbrice/project-api_spec/issues)


## License

Apache License 2.0. See [LICENSE](LICENSE).

## Contact

- [Portfolio](https://maebrieporfolio.vercel.app/)
- [GitHub](https://github.com/frckbrice)
- [LinkedIn](https://linkedin.com/in/avombrice)

---

OpenAPI 3.1.0, Redocly, Docker, GitHub Actions, TypeScript.
