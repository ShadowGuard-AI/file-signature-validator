![Banner](banner.png)

# file-signature-validator
Verifies digital signatures of files against a provided public key, ensuring authenticity and integrity. Focused on File operations and analysis.

## Install
```bash
git clone https://github.com/ShadowGuard-AI/file-signature-validator.git
cd file-signature-validator
```

Python 3, standard library only, plus the system `openssl` executable. There is nothing to install.

## Usage
```bash
python3 main.py FILE_PATH SIGNATURE_FILE PUBLIC_KEY [options]
```

Example, with a signature made by openssl:
```bash
openssl dgst -sha256 -sign private.pem -out file.txt.sig file.txt
python3 main.py file.txt file.txt.sig public_key.pem
```
```
Signature is valid.
```

## Parameters
- `file_path`: Path to the file to verify. Required.
- `signature_file`: Path to the signature file. Required.
- `public_key`: Path to the PEM public key file. Required. Note: the openssl call takes a PEM public key, so a certificate file passed as-is fails; extract its key first.
- `--hash_algorithm`: Hash algorithm to use for verification. Choices: `sha256`, `sha512`. Default: `sha256`.
- `--openssl_path`: Path to the openssl executable. Default: `openssl`.

## Exit codes
- `0`: the signature is valid.
- `1`: the signature is invalid, a file is missing, or openssl reports an error. Every failure prints the same "Signature is invalid." line; the log holds the reason.

## License
MIT. See [LICENSE](LICENSE).
