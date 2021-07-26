---
title: Reference
lang: en-US
sidebarDepth: 2
meta:
  - name: keywords
    content: configuration options settings Pomerium enterprise console
---

# Pomerium Enterprise Console Settings

The Pomerium Enterprise Console is initially configured using a configuration file ([YAML]/[JSON]/[TOML]) or environment variables. In general, environmental variable keys are identical to config file keys but are uppercase.

 If you are coming from a Kubernetes or docker background this should feel familiar. If not, check out the following primers.

- [Store config in the environment](https://12factor.net/config)
- [Kubernetes: Environment variables](https://kubernetes.io/docs/tasks/inject-data-application/define-environment-variable-container/)
- [Kubernetes: Config Maps](https://kubernetes.io/docs/tasks/configure-pod-container/configure-pod-configmap/)
- [Docker: Environment variables](https://docs.docker.com/compose/environment-variables/)

Using both [environmental variables] and config file keys is allowed and encouraged (for instance, secret keys are probably best set as environmental variables). However, if duplicate configuration keys are found, environment variables take precedence.

Additional configuration and the setting of routes and policies is performed through the web user interface (**UI**).


## Configuration Settings
These configuration values are set in the `config.yaml` file for Pomerium Enterprise Console, or as environment variables. Once the console is accessible, configuration is adjusted through the web UI.



### User Impersonation
@travis fill me with delicious data!


## Reports

### Traffic

### Runtime

### Sessions

### Events

### Deployments

## Manage

### Routes
A Route provides access to a service through Pomerium.


#### General
The **General** tab defines the route path, both from the internet and to the internal service, and the policies attached. Note that policies enforced on a Namespace the Route resides in will also be applied.


##### Name

##### From

##### To

##### Redirect

##### Policies

##### Pass Identity Headers

##### Enable Google Cloud Serverless Authentication

#### Matchers

#### Rewrite

#### Timeouts

#### Headers

#### Load Balancer

### Policies
A Policy defines what permissions a set of users or groups has. Policies are applied to [Namespaces](#namespaces) or [Routes](#routes) to associate the set of permissions with a service or set of service, completing the authentication model.

::: tip
This is a separate concept from [policies](../reference/#policy) in the non-enterprise model. In open-source Pomerium, the `policy` block defines both routes and access.
:::

Policies can be constructed three ways:

#### Web UI

From the **BUILDER** tab, users can add allow or deny blocks to a policy, containing and/or/not/nor logic to allow or deny sets of users and groups.

![A policy being constructed in Pomerium Enterprise console allowing a single user access](./img/example-policy-single-user.png)

#### Pomerium Policy Language

From the **EDITOR** tab users can write policies in Pomerium Policy Language (**PPL**), a YAML-based notation.

![A policy as viewed from the editor tab](./img/example-policy-editor.png)

#### Rego

For those using [OPA](https://www.openpolicyagent.org/), the **REGO** tab will accept policies written in Rego.

::: tip
A policy can only support PPL or Rego. Once one is set, the other tab is disabled.
:::

#### Overrides
- **Any Authenticated User**: This setting will allow access to a route with this policy attached to any user who can authenticate to your Identity Provider (**IdP**).
- **CORS Preflight**: 
- **Public Access**: This setting allows complete, unrestricted access to an associated route. Use this setting with caution.


### Certificates

## Configure

### Settings

#### Global

#### Cookies

#### Timeouts

#### GRPC

#### Tracing

#### Authenticate

#### Authorize

#### Proxy

### Service Accounts
<!-- Explain Service Accounts -->


### Namespaces
A Namespace is a collection of users, groups, routes, and policies that allows system administrators to organize, manage, and delegate permissions across their infrastructure.

- Policies can be optional or enforced on a Namespace, and they can be nested to create inheritance.
- Users or groups can be granted permission to edit access to routes within a Namespace, allowing them self-serve access to the routes critical to their work.


[base64 encoded]: https://en.wikipedia.org/wiki/Base64
[elliptic curve]: https://wiki.openssl.org/index.php/Command_Line_Elliptic_Curve_Operations#Generating_EC_Keys_and_Parameters
[environmental variables]: https://en.wikipedia.org/wiki/Environment_variable
[identity provider]: ../docs/identity-providers/
[json]: https://en.wikipedia.org/wiki/JSON
[letsencrypt]: https://letsencrypt.org/
[oidc rfc]: https://openid.net/specs/openid-connect-core-1_0.html#AuthRequest
[okta]: ../docs/identity-providers/okta.md
[script]: https://github.com/pomerium/pomerium/blob/master/scripts/generate_wildcard_cert.sh
[signed headers]: ../docs/topics/getting-users-identity.md
[toml]: https://en.wikipedia.org/wiki/TOML
[yaml]: https://en.wikipedia.org/wiki/YAML