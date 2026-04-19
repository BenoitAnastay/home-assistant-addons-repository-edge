# Changelog since v3.1.3
- 🔧Add an option to remove port from path for reverse proxies (#385)

This pull request adds support for improved reverse proxy handling in the Paperless add-on, specifically addressing scenarios where an external reverse proxy terminates HTTPS on a different host. The main change introduces a new configuration option to control whether the internal port is included in the `X-Forwarded-Host` header, preventing port leakage in generated URLs (such as OIDC redirect URIs). Documentation and translations have also been updated to explain and support this new feature.

**Reverse proxy support improvements:**

* Added a new `x_forwarded_host_no_port` configuration option to allow forwarding `X-Forwarded-Host` without the internal port, for use with external reverse proxies on a different host. [[1]](diffhunk://#diff-ffc7d11b6c80a48a5a6db02737b6e87361a3a94a4e545016ed4f6f637607d94eR60) [[2]](diffhunk://#diff-b4271badfa189f398468a4fb67e3b47eb6dc6f4a0daaa4c6ccff258369e6b8eaR64-R73)
* Updated the NGINX template (`direct.gtpl`) to conditionally set the `X-Forwarded-Host` header based on the new option, either including or omitting the port.
* Modified the NGINX initialization script to pass the new configuration option to the template engine.

**Documentation and translation updates:**

* Extended documentation in `DOCS.md` to explain the new option, including when and how to use it, and provided environment variable examples for correct Paperless configuration.
* Added English translation strings for the new option, including a detailed description to guide users.

Co-authored-by: Benoit Anastay <45088785+BenoitAnastay@users.noreply.github.com> 
