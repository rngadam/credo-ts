# Tails retrieval 

## Context

We walk through the steps and sequence of when the tails file is retrieved.

For information on where the tails file is stored, see [storage](storage.md)

## Tails service references

[export async function getRevocationRegistriesForRequest(](https://github.com/rngadam/credo-ts/blob/a65a9c39879e83975de25022bd962a9ed16bcec3/packages/anoncreds/src/utils/getRevocationRegistries.ts#L12)

https://github.com/rngadam/credo-ts/blob/a65a9c39879e83975de25022bd962a9ed16bcec3/packages/anoncreds/src/utils/getRevocationRegistries.ts#L93-L96

getTailsFile either retrieves the tails file from cache or downloads it (and stores it to cache)

## AnonCreds (similar process for the LegacyIndyProofFormatService.ts)

createProof is where the tails file is retrieved (possibly for the first time):

[private async createProof(](https://github.com/rngadam/credo-ts/blob/a65a9c39879e83975de25022bd962a9ed16bcec3/packages/anoncreds/src/formats/AnonCredsProofFormatService.ts#L391-L392)

https://github.com/rngadam/credo-ts/blob/a65a9c39879e83975de25022bd962a9ed16bcec3/packages/anoncreds/src/formats/AnonCredsProofFormatService.ts#L412-L416

createProof is called in an acceptRequest:

[public async acceptRequest(](https://github.com/rngadam/credo-ts/blob/a65a9c39879e83975de25022bd962a9ed16bcec3/packages/anoncreds/src/formats/AnonCredsProofFormatService.ts#L153)

the actual proof creation is done in the thin layer over the implementation (Example anoncreds-rs):

[createProof](https://github.com/rngadam/credo-ts/blob/a65a9c39879e83975de25022bd962a9ed16bcec3/packages/anoncreds/src/anoncreds-rs/AnonCredsRsHolderService.ts)

where the record information (including revocationRegistryId, credentialRevocationId) are extracted from the credentialRecord and proofRequest)

https://github.com/rngadam/credo-ts/blob/a65a9c39879e83975de25022bd962a9ed16bcec3/packages/anoncreds/src/anoncreds-rs/AnonCredsRsHolderService.ts#L146-L149

if there is indeed some revocation information, the presence of the revocation registry is checked, the status list retrieved and calls goes out to the implementation (in Rust):

https://github.com/rngadam/credo-ts/blob/a65a9c39879e83975de25022bd962a9ed16bcec3/packages/anoncreds/src/anoncreds-rs/AnonCredsRsHolderService.ts#L158-L182
