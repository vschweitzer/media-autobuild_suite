# Custom FFmpeg autobuild suite

This is a version of the media-autobuild_suite, modified to build
non-standard/non-newest versions of FFmpeg.

## Fallback

If all else fails, use the suite located at
`\\nativewavesmedia\software\ffmpeg-builds\custom\nw_mabs.zip`.
Unpack this into any short path like `C:\`. If you have problems with
authentication, check [AUTHENTICATION.md](./AUTHENTICATION.md).

This version has worked before. If this compilation fails, a new error
is occurring.

## Modifications

The following things have been changed to allow for non-standard
compilations:

### Skip msys update

(Most) Msys updates can be disabled by settings `skip_update_flag` in
`build/media-suite_update.sh` to `1`. Msys *will* run some updates on
first start. This cannot be skipped.

### git paths

The git paths for most repositories have been put into
`build/media-suite_urls.sh`. Some URLs have been left in, because they
contain variables.

To change repository (for example, to
a custom FFmpeg repository) or the commit (to freeze the version),
change the URL and postfix respectively. The postfix, if not empty, must
start with `#`. If a non-public repository hosted on github is used, you
*must* use the `ssh` url, as http authentication is deprecated. For more
info on `ssh` auth read [AUTHENTICATION.md](./AUTHENTICATION.md).

### Versions and freezing

To build FFmpeg versions that differ from HEAD, dependency versions
sometimes have to be frozen. Setting a specific branch or commit can
be done by changing the postfix in `build/media-suite_urls.sh`,
for example:
 * `"commit=<commit_id>"`
 * `"branch=<branch>"`

To get information about the software versions used in a specific build,
version info is dumped into `build/versions.csv`. They follow the
pattern of `<url>;<ref (mostly branch or LATEST)>;>commit>`.
