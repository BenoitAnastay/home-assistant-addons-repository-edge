# Changelog since v4.0.6
- ⬆️ Update debian_13/nginx to v1.26.3-3+deb13u11 (#470)

Co-authored-by: renovate[bot] <29139614+renovate[bot]@users.noreply.github.com> 
- ⬆️ Update paperless-ngx/paperless-ngx to v3.5.1 (#468)

Co-authored-by: renovate[bot] <29139614+renovate[bot]@users.noreply.github.com> 
- 🐛 Restore copy of upstream docker rootfs (#469)

The ImageMagick removal in #466 also dropped the step that copies
/usr/src/paperless/docker/rootfs into the image. Without it
/usr/local/bin/deduplicate.py is missing and the build fails with
exit code 127. Restore the copy without the ImageMagick policy part.

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com> 
- ⬆️ Update ZLIB_VERSION in Dockerfile (#467) 
- 💚 remove ImageMagik (#466)

Removed ImageMagick installation and related configuration steps from the Dockerfile. 
- ⬆️ Update paperless-ngx/paperless-ngx to v3.4.2 (#462)

Co-authored-by: renovate[bot] <29139614+renovate[bot]@users.noreply.github.com> 
- ⬆️ Update ghcr.io/hassio-addons/debian-base Docker tag to v9.5.2 (#465)

Co-authored-by: renovate[bot] <29139614+renovate[bot]@users.noreply.github.com> 
- ⬆️ Update debian_13/tzdata to v2026f-0+deb13u1 (#463)

Co-authored-by: renovate[bot] <29139614+renovate[bot]@users.noreply.github.com> 
- ⬆️ Update debian_13/imagemagick to v8:7.1.1.43+dfsg1-1+deb13u13 (#461)

Co-authored-by: renovate[bot] <29139614+renovate[bot]@users.noreply.github.com> 
