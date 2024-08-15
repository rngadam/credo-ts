# Witness

## the witness value 

witness is part of the AnonCredsCredential interface:

https://github.com/rngadam/credo-ts/blob/a65a9c39879e83975de25022bd962a9ed16bcec3/packages/anoncreds/src/models/exchange.ts#L48-L57

as shown in the indy sdk to askar format conversion, the witness is dropped in the AnonCredsCredentialRecord:

https://github.com/rngadam/credo-ts/blob/a65a9c39879e83975de25022bd962a9ed16bcec3/packages/indy-sdk-to-askar-migration/src/IndySdkToAskarMigrationUpdater.ts#L382-L408

anoncreds-rs does validate for witness value if revocation registry and revocation registry id is present:

https://github.com/hyperledger/anoncreds-rs/blob/44a22edc49275f4ad0ea805ae9b033d86c22b405/src/data_types/credential.rs#L64-L66

## Proof

in CredentialSignatureProofValue, witness may be none:

https://github.com/hyperledger/anoncreds-rs/blob/44a22edc49275f4ad0ea805ae9b033d86c22b405/src/data_types/w3c/proof.rs#L263-L275

Prover recomputes witness here:

https://github.com/hyperledger/anoncreds-rs/blob/44a22edc49275f4ad0ea805ae9b033d86c22b405/src/services/prover.rs#L607-L635

## Issuance

the witness is created using CLCredentialIssuer:

https://github.com/hyperledger/anoncreds-rs/blob/44a22edc49275f4ad0ea805ae9b033d86c22b405/src/services/issuer.rs#L716-L722

which in turns calls Issuer::sign_credential_with_revoc:

https://github.com/hyperledger/anoncreds-rs/blob/44a22edc49275f4ad0ea805ae9b033d86c22b405/src/services/issuer.rs#L814-L829
