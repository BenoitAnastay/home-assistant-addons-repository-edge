# Changelog since v3.1.3
- 🐛 Fix libpq version management and suppress Renovate no-result warnings (#393)

Extracts LIBPQ_VERSION as a single ENV variable replacing two hardcoded
17.10-0+deb13u1 literals in RUNTIME_PACKAGES and BUILD_PACKAGES, and
adds a packageRules entry in renovate.json to disable the auto-detected
debian_13/libpq5 and debian_13/libpq-dev lookups that produce no-result
warnings (these are binary packages from the postgresql-17 source and
are not tracked as standalone projects in repology).

Co-authored-by: Claude <noreply@anthropic.com> 
- 🐛 Resolve Tika-Gotenberg hostname dynamically from container slug (#392)

* fix: resolve Tika-Gotenberg hostname dynamically from container slug

The Tika-Gotenberg sibling addon hostname was hardcoded as
ca5234a0-tika-gotenberg. The repo slug (ca5234a0) is computed by the
HA Supervisor from the repository URL and is not guaranteed to be
stable across installations or forks.

Instead, derive the repo slug at runtime by stripping the known addon
suffix (-paperless-ngx) from the current container hostname, then
construct the Tika-Gotenberg hostname using the same prefix. This
ensures both addons resolve each other correctly regardless of which
slug the Supervisor assigned.

Closes #283
Closes #349

https://claude.ai/code/session_01DgjYEbo1GRrkQuipkTh1gx

* fix: drop stale version pins that break apt-get on Debian 13 trixie

Two categories of pinned packages were causing the Docker build to fail
with exit code 100 (apt-get package not found):

1. libxslt1.1=1.1.35-1.2+deb13u2
   The package name contains a '.' which is not matched by Renovate's
   inline regex ([a-z0-9][a-z0-9-]+), so it was never auto-updated.
   Debian 13 trixie has since moved to libxslt 1.1.39+. The version
   pin is dropped and replaced with a Renovate-tracked ENV var
   (LIBXSLT_VERSION) so it can be re-pinned once Renovate confirms
   the current version via repology depName=debian_13/libxslt1.

2. unpaper / pngquant with binary-rebuild suffixes (+b2, +b3, +b1)
   Debian trixie rebuilds packages frequently; the +bN suffix changes
   with every rebuild and was not tracked by Renovate at all.
   Version pins are removed; the arch-specific case arms are merged
   into a single pattern since both now install without version.

https://claude.ai/code/session_01DgjYEbo1GRrkQuipkTh1gx

* ⬆️ Update libpq5 and libpq-dev to 17.10-0+deb13u1

---------

Co-authored-by: Claude <noreply@anthropic.com> 
- ⬆️ Update debian_13/tzdata to v2026b-0+deb13u1 (#391)

Co-authored-by: renovate[bot] <29139614+renovate[bot]@users.noreply.github.com> 
- ⬆️ Update debian_13/curl to v8.14.1-2+deb13u3 (#389)

Co-authored-by: renovate[bot] <29139614+renovate[bot]@users.noreply.github.com> 
- ⬆️ Update debian_13/nginx to v1.26.3-3+deb13u5 (#390)

Co-authored-by: renovate[bot] <29139614+renovate[bot]@users.noreply.github.com> 
- ⬆️ Update paperless-ngx/paperless-ngx to v2.20.15 (#386)

Co-authored-by: renovate[bot] <29139614+renovate[bot]@users.noreply.github.com> 
- ⬆️ Update debian_13/imagemagick to v8:7.1.1.43+dfsg1-1+deb13u8 (#387)

Co-authored-by: renovate[bot] <29139614+renovate[bot]@users.noreply.github.com> 
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
