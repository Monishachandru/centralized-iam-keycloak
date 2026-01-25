# Flask Application Setup – SSO Integration

## Overview

This module covers the setup of a lightweight **Flask** application to integrate with Keycloak for Single Sign-On (SSO) using **OpenID Connect (OIDC)**. The setup establishes the foundation for testing centralized authentication flows.

---

## Environment Setup

A Python virtual environment is used to isolate dependencies and ensure consistency.

### Steps Performed

```bash
mkdir ~/sso-app
cd ~/sso-app
python3 -m venv venv
source venv/bin/activate
```

---

## Dependency Installation

The required Python packages were installed using `pip`:

```bash
pip install flask authlib
```

### Installed Components

* **Flask** – Lightweight web framework for building the application
* **Authlib** – OAuth 2.0 / OpenID Connect client library

---

## Outcome

The Flask development environment was successfully configured with all required dependencies. The application is ready for implementing Keycloak-based SSO and role-aware access control.
