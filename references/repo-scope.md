# Repo Scope

This skill is intentionally narrow. Treat the following directories as the primary search space:

## Primary backend project

- `vendor-payment-engine-blazor/vendor_payment_system/Controllers`
- `vendor-payment-engine-blazor/vendor_payment_system/ServiceLayer/Interfaces`
- `vendor-payment-engine-blazor/vendor_payment_system/ServiceLayer/Services`
- `vendor-payment-engine-blazor/vendor_payment_system/DataLayer`
- `vendor-payment-engine-blazor/vendor_payment_system/Data`
- `vendor-payment-engine-blazor/vendor_payment_system/Binders`
- `vendor-payment-engine-blazor/vendor_payment_system/Configuration`
- `vendor-payment-engine-blazor/vendor_payment_system/Utils`
- `vendor-payment-engine-blazor/vendor_payment_system/Program.cs`

## Shared project

- `vendor-payment-engine-blazor/vendor_payment_system.shared/DTOs`
- `vendor-payment-engine-blazor/vendor_payment_system.shared/Domain`
- `vendor-payment-engine-blazor/vendor_payment_system.shared/Models`
- `vendor-payment-engine-blazor/vendor_payment_system.shared/Authorization`
- `vendor-payment-engine-blazor/vendor_payment_system.shared/Exceptions`
- `vendor-payment-engine-blazor/vendor_payment_system.shared/Utils`
- `vendor-payment-engine-blazor/vendor_payment_system.shared/Service`

## Common search anchors

Use these patterns first:

- Route lookup:
  - `\[Http(Get|Post|Put|Patch|Delete)`
  - `\[Route\(`
  - `class .*Controller`
- DI lookup:
  - `builder.Services.AddScoped`
  - `builder.Services.AddSingleton`
  - `builder.Services.AddTransient`
- Controller-to-service lookup:
  - controller constructor parameters
  - `_serviceName.`
- Interface-to-implementation lookup:
  - `AddScoped<I`
  - matching interface names in `ServiceLayer/Interfaces`
- Repository lookup:
  - `Repository`
  - `DbContext`
  - `_context.`
- Shared types lookup:
  - DTO name
  - request model name
  - response model name

## Scope exclusions

Ignore by default:

- `vendor_payment_system.client`
- build artifacts such as `bin`, `obj`, `.vs`
- docs, prompts, reports, and ad-hoc helper files unless the user asks about them directly

## Notes specific to this codebase

- The backend is ASP.NET Core with controller-based APIs plus a large dependency registration block in `Program.cs`.
- Service implementations mostly live in `ServiceLayer/Services`.
- Interfaces mostly live in `ServiceLayer/Interfaces`.
- Shared request and response shapes are spread across both `DTOs` and `Domain`.
- Some namespaces are inconsistent; trust actual registrations and usages over naming alone.
