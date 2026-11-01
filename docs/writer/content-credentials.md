# Content Credentials

Some cameras, the Leica M11-P among them, sign each photo with
[Content Credentials](https://contentcredentials.org/), a record inside the file
of where the photo came from. Any change to the file, even to its metadata,
makes that signature fail. Writing your notes into such a file would therefore
break the camera's credentials.

Shot Notes does not break them. When a file has credentials, the writer adds a
new signed record on top of the camera's, and leaves the image data alone. The
new record holds the camera's as its parent and says what changed, so that it
reads: the camera captured this, then Shot Notes changed these fields.

It has been tried on Leica M11-P DNG files, and on a JPEG, an iPhone HEIC and a
large TIFF.

## What you can choose

The writer looks for credentials in each file before it writes anything, and
tells you which files have them. You then choose what to do with those files:

| Choice | What happens |
|---|---|
| **Add a new credential** (the default) | The notes are written into the file, and a new credential is signed that keeps the camera's as its parent. |
| **Keep it in a `.c2pa` file** | The notes are written into the file, and the new credential is kept in a `.c2pa` file beside the image. The camera's credential is not in the file any more. |
| **An XMP sidecar only** | The file and its credentials are not touched. The notes go into a sidecar. Lightroom Classic ignores the aperture and focal length of a sidecar for a DNG. |

Only files that have credentials are signed. Without the Content Credentials
helper or a certificate, the first two choices are refused and nothing is
written: choose the sidecar, or make or choose a certificate.

![The Write step for files with Content Credentials: the choices, and the credentials in the file now and after writing](../screenshots/writer-write-credentials-light.svg#only-light){ loading=lazy }
![The Write step for files with Content Credentials: the choices, and the credentials in the file now and after writing](../screenshots/writer-write-credentials-dark.svg#only-dark){ loading=lazy }

## The certificate

Signing needs a certificate and a private key. You choose between:

- **Your own.** A certificate and key as PEM files, from an authority on the
  C2PA trust list if you want programs that check credentials to trust the
  signer.
- **One made for you.** The writer asks for your name and some details (only the
  name is needed) and makes a self-signed certificate on your computer, only
  when you ask. In the desktop app it is in Settings, under Certificate, and it is
  offered when you write a file with credentials. With the command-line tool,
  run `shotnotes certificate`. The desktop app, the command-line tool and the
  Lightroom plugin share it.

Things to know about a certificate made for you:

- Programs that check credentials will show the signer as **not recognised**,
  because no authority on the trust list vouches for it. The name in it is only
  what you typed. The camera's original signature is still shown as the
  camera's.
- Making a new one deletes the earlier one and its private key, and says so
  first. A certificate and key you brought are never touched.
- The private key is a file in your user folder on this computer. Keep it
  private, as you would a password.

## If you would rather not sign

Choose the XMP sidecar. Nothing in the image file changes, so the camera's
credentials stay valid. The cost is that Lightroom Classic reads the lens name,
keywords and description from the sidecar, but takes the aperture and the focal
length of a DNG from the file itself.
