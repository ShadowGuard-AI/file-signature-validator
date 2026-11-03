![Banner](banner.png)

# file-signature-validator
Verifies digital signatures of files against a provided public key or certificate, ensuring authenticity and integrity. Focused on File operations and analysis.

## Install
`git clone https://github.com/ShadowGuard-AI/file-signature-validator`

## Usage
`python3 main.py FILE_PATH SIGNATURE_FILE PUBLIC_KEY [options]`

Example, with a signature made by openssl:

`python3 main.py myfile.txt myfile.txt.sig public_key.pem`

`python3 main.py myfile.txt myfile.txt.sig public_key.pem --hash_algorithm sha512`

`python3 main.py myfile.txt myfile.txt.sig public_key.pem --openssl_path /usr/local/bin/openssl`

## Parameters
- `file_path`: Path to the file to verify. Required.
- `signature_file`: Path to the signature file. Required.
- `public_key`: Path to the public key or certificate file. Required.
- `--hash_algorithm`: Hash algorithm to use for verification. Choices: sha256, sha512. Default: sha256.
- `--openssl_path`: Path to the openssl executable. Default: openssl.

## Verified in this wave
`python3 main.py --help` prints the form above. A live openssl run verified a valid RSA signature (exit 0, "Signature is valid."), a tampered file (exit 1, "Signature is invalid."), and a missing input file (exit 1, "Signature is invalid."). Note: openssl `dgst -verify` expects a raw public key in PEM form, so a certificate file passed as is does not verify here; extract the key from the certificate first. All failures print the same invalid line and exit 1; the log holds the reason.

## License
See LICENSE.
