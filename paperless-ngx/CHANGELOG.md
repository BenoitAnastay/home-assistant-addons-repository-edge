# Changelog since v3.1.4
- ✨ Updates running scripts for paperless v3 (#411) 
- 💚 Fix CI for v3.0.0 (#410)

* 💚 Fix CI for v3.0.0 
- ⬆️ Update redis version to 5:8.0.2-3+deb13u2 and poppler version to 25.03.0-5+deb13u4 (#409)

* ⬆️ Update redis version to 5:8.0.2-3+deb13u2

* ⬆️ Update poppler version to 25.03.0-5+deb13u4 
- ⬆️ Update paperless-ngx/paperless-ngx to v3 (#407)

Co-authored-by: renovate[bot] <29139614+renovate[bot]@users.noreply.github.com> 
- ⬆️ Update debian_13/curl to v8.14.1-2+deb13u4 (#403)

Co-authored-by: renovate[bot] <29139614+renovate[bot]@users.noreply.github.com> 
- ⬆️ Update debian_13/libxml2 to v2.12.7+dfsg+really2.9.14-2.1+deb13u3 (#404)

Co-authored-by: renovate[bot] <29139614+renovate[bot]@users.noreply.github.com> 
- ⬆️ Update debian_13/xz-utils to v5.8.1-1+deb13u1 (#405)

Co-authored-by: renovate[bot] <29139614+renovate[bot]@users.noreply.github.com> 
- 🐛 Fix ingress SSO 403 lockout when no superuser exists (#400)

With ingress_auth enabled, the remote-user middleware auto-created a
permissionless user on the first ingress request, hiding the upstream
first-account creation screen forever and locking the user out with
403 Forbidden errors (#306).

- Defer SSO while no account exists so the first-account screen stays
  reachable; SSO activates on the next add-on restart.
- Promote the single SSO-created user to superuser at startup when no
  superuser exists, healing installations already stuck at 403.
- Remove the stale default_superuser option from DOCS and translations,
  document the ingress_auth first-account flow instead.


Claude-Session: https://claude.ai/code/session_01JT2QsdSaPh3amhtyc1wpy2

Co-authored-by: Claude <noreply@anthropic.com> 
- ⬆️ Update debian_13/imagemagick to v8:7.1.1.43+dfsg1-1+deb13u11 (#402)

Co-authored-by: renovate[bot] <29139614+renovate[bot]@users.noreply.github.com> 
- ⬆️ Update debian_13/nginx to v1.26.3-3+deb13u7 (#401)

Co-authored-by: renovate[bot] <29139614+renovate[bot]@users.noreply.github.com> 
