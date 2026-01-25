## Configuration

### Realms

A **Realm** in Keycloak represents an isolated security domain.

This setup supports:

* Multiple environments (dev, staging, prod)
* Multi-tenancy (one realm per tenant)

Example realms:

* `master` (administration only)
* `company-dev`
* `company-prod`

---

### Clients

Clients represent applications or services that rely on Keycloak for authentication.

Supported client types:

* **Public clients** (SPAs, mobile apps)
* **Confidential clients** (backend services, APIs)
* **Service accounts** (machine-to-machine access)

Example clients:

* `web-portal`
* `admin-dashboard`
* `orders-api`

---

### Roles & RBAC

Role-Based Access Control (RBAC) is implemented using:

* **Realm Roles** – global roles (e.g. `admin`, `user`)
* **Client Roles** – application-specific roles (e.g. `orders.read`)
* **Groups** – role aggregation and user organization

Example:

* `admin` → full access
* `manager` → read/write access
* `user` → read-only access

---

### Multi-Factor Authentication (MFA)

MFA is enforced using **One-Time Passwords (OTP)**:

* TOTP (RFC 6238)
* Compatible with Google Authenticator, Authy, Microsoft Authenticator

MFA can be:

* Optional
* Required for specific roles
* Enforced globally per realm

---

## Authentication Flow

### Authorization Code Flow (OIDC)

1. User accesses an application
2. Application redirects user to Keycloak login page
3. User authenticates (password + OTP if enabled)
4. Keycloak issues authorization code
5. Application exchanges code for tokens
6. Application uses JWT access token for API calls

---

## Token Management

Keycloak issues:

* **Access Token (JWT)** – short-lived
* **Refresh Token** – long-lived
* **ID Token** – user identity information

JWT Claims may include:

* User ID
* Username
* Email
* Assigned roles
* Custom attributes

---

## Securing APIs

APIs validate JWT tokens issued by Keycloak:

* Verify signature using Keycloak public key
* Validate issuer, audience, and expiration
* Enforce authorization using roles/claims

Popular integrations:

* Spring Boot (Spring Security)
* Node.js (Passport.js, Keycloak adapters)
* .NET (Microsoft.Identity)
* Kubernetes (OIDC integration)

---

## Environment Configuration

Common environment variables:

```env
KEYCLOAK_ADMIN=admin
KEYCLOAK_ADMIN_PASSWORD=admin
KC_DB=postgres
KC_DB_URL=jdbc:postgresql://db:5432/keycloak
KC_DB_USERNAME=keycloak
KC_DB_PASSWORD=keycloak
```
