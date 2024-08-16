# Witness

## the witness value 

witness is part of the AnonCredsCredential interface:

https://github.com/rngadam/credo-ts/blob/a65a9c39879e83975de25022bd962a9ed16bcec3/packages/anoncreds/src/models/exchange.ts#L48-L57

Which is part of AnonCredsCredentialRecordProps

https://github.com/rngadam/credo-ts/blob/a65a9c39879e83975de25022bd962a9ed16bcec3/packages/anoncreds/src/repository/AnonCredsCredentialRecord.ts#L6-L18

itself combined into AnonCredsCredentialRecord:

https://github.com/rngadam/credo-ts/blob/a65a9c39879e83975de25022bd962a9ed16bcec3/packages/anoncreds/src/repository/AnonCredsCredentialRecord.ts#L41-L44

as shown in the indy sdk to askar format conversion, the witness is kept within data in the AnonCredsCredentialRecord:

https://github.com/rngadam/credo-ts/blob/a65a9c39879e83975de25022bd962a9ed16bcec3/packages/indy-sdk-to-askar-migration/src/IndySdkToAskarMigrationUpdater.ts#L382-L408

AnonCredsCredentialRecord are managed by a Repository that offers CRUD operations, using an underlying StorageService 

https://github.com/rngadam/credo-ts/blob/a65a9c39879e83975de25022bd962a9ed16bcec3/packages/core/src/storage/Repository.ts#L28-L38

one storage service is the AskarStorageService:

https://github.com/rngadam/credo-ts/blob/a65a9c39879e83975de25022bd962a9ed16bcec3/packages/askar/src/storage/AskarStorageService.ts#L19-L22

which uses an AskarProfileWallet.

continues in anoncreds-rs: https://github.com/rngadam/anoncreds-rs/blob/main/docs/witness.md

