# GPG Key Repository

This repository contains various GPG keys and related signatures. It is organized to help manage and verify GPG keys efficiently.

## Directory Structure

- **KeySignatures/**: This directory contains signatures of my public keys by others.
  
  examples: 
  
  - `my_KeyID_signed_by_alice.asc`: My public key signed by Alice.
  - `my_KeyID_signed_by_bob.asc`: My public key signed by Bob.
  
- **MyPubkeys/**: This directory contains my public GPG keys.
  
  - `KeyID_myemail@example.com.asc`: My public key.
  
- **SignedPubkeys/**: This directory contains public keys of other people that I have signed.
  
  examples: 
  
  - `alice_KeyID_signed_by_me.asc`: Alice's public key signed by me.
  - `bob_KeyID_signed_by_me.asc`: Bob's public key signed by me.

KeyID: Short Pubkey ID.

## Usage

### Importing My Public Key

To import my public keys into your GPG keyring, you can use the following command:

```shell
gpg --import MyPubkeys/KeyID_myemail@example.com.asc
```

### Verifying a Signed Key

To verify a key signed by me, you can use the following command:

```shell
gpg --import SignedPubkeys/alice_pubkey_signed_by_me.asc
gpg --check-sigs alice@example.com
```

Replace `alice@example.com` with the appropriate email address associated with the key you are verifying.

### Adding Your Signature to My Key

If you'd like to sign my public key and send the signature back to me, follow these steps:

1. Import my public key:

    ```shell
    gpg --import MyPubkeys/KeyID_myemail@example.com.asc
    ```

2. Sign my public key:

    ```shell
    gpg --sign-key myemail@example.com
    ```

3. Export the signed key:

    ```shell
    gpg --armor --export myemail@example.com > my_pubkey_signed_by_<your_username>.asc
    ```

4. Send the signed key back to me via a Pull Request (PR):

    - Fork this repository.
    - Add your signed key file to the `KeySignatures/` directory.
    - Name the file `my_pubkey_signed_by_<your_username>.asc`.
    - Create a PR with a description of your changes.
    - Delete your fork (optional).

## Contributing

Feel free to open issues or pull requests if you find any discrepancies or have suggestions for improvement. If you have signed my public key, please submit a PR as described above.