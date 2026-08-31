# Changelog since v4.0.1
- ⬆️ Update paperless-ngx/paperless-ngx to v3.1.1 (#427)

Co-authored-by: renovate[bot] <29139614+renovate[bot]@users.noreply.github.com> 
- 🎨 replace `bashio::addon.whetever` by `bashio::app.whetever` (#424)

* change addon. to app.

* change addon. to app.

* change addon. to app. 
- 🐛 Increase Nginx proxy timeouts to prevent 504 errors (#425)

* fix: increase Nginx proxy timeouts to 300s to prevent 504 errors during long LLM inferences

* Increase proxy timeouts for long-running requests

Updated proxy timeouts to accommodate long-running requests.

* Adjust Nginx proxy timeouts for AI inference

Increase proxy read and send timeouts for long-running requests. 
