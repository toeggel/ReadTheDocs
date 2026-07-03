# Auth

```text
User Account
    ↓
digitale Identität eines Menschen

Service Principal
    ↓
digitale Identität einer Anwendung
```

We still need a password or secret for the Service Principal and have hence all the issues that come with it (e.g. protection, rotation, ..). 
Using a Managed Identity solves this issue. Azure automatically generates and handles Identity, Credential, Lifecycle, Rotation for a Azure Ressource.
Guideline: Everything that runs within Azure should use Managed Identity. Things outside of azure probably need a service principal

