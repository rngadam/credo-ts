# Storage

## Purpose

We dig into where the actual tails files are stored on mobile devices for Credo React-Native applications.

## Notes

* source embedding only work in the original repo
* to preview the reference properly, we work from a fork 
* will have to be updated from org rngadam to openwallet-foundation before being merged back

see: https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/creating-a-permanent-link-to-a-code-snippet

## Tails files

### Implementation of BasicTailsFileService

* [export class InMemoryTailsFileService extends BasicTailsFileService {](https://github.com/rngadam/credo-ts/blob/a65a9c39879e83975de25022bd962a9ed16bcec3/packages/anoncreds/tests/InMemoryTailsFileService.ts#L8-L9)

### BasicTailsFileService

[public async getTailsBasePath(agentContext: AgentContext) {](https://github.com/rngadam/credo-ts/blob/a65a9c39879e83975de25022bd962a9ed16bcec3/packages/anoncreds/src/services/tails/BasicTailsFileService.ts#L14-L21)

https://github.com/rngadam/credo-ts/blob/a65a9c39879e83975de25022bd962a9ed16bcec3/packages/anoncreds/src/services/tails/BasicTailsFileService.ts#L14-L21

note that we have this extra file appended because the createDirectory finds out the path from a full file path:

https://github.com/rngadam/credo-ts/blob/a65a9c39879e83975de25022bd962a9ed16bcec3/packages/react-native/src/ReactNativeFileSystem.ts#L42-L44

[protected async getTailsFilePath(agentContext: AgentContext, tailsHash: string) {](https://github.com/rngadam/credo-ts/blob/a65a9c39879e83975de25022bd962a9ed16bcec3/packages/anoncreds/src/services/tails/BasicTailsFileService.ts#L79-L82)

https://github.com/rngadam/credo-ts/blob/a09315070dd6914b8d51e0d94005e11d7a0f49cc/packages/anoncreds/src/services/tails/BasicTailsFileService.ts#L79-L81

[public constructor(options?: { tailsDirectoryPath?: string; tailsServerBaseUrl?: string }) {](https://github.com/rngadam/credo-ts/blob/a65a9c39879e83975de25022bd962a9ed16bcec3/packages/anoncreds/src/services/tails/BasicTailsFileService.ts#L10-L12)

https://github.com/rngadam/credo-ts/blob/a65a9c39879e83975de25022bd962a9ed16bcec3/packages/anoncreds/src/services/tails/BasicTailsFileService.ts#L10-L12

### Usage in AnonCredsModuleConfig.ts

No configuration is set, so we can assume that fileSystem.cachePath is used, retrieved from the dependency injection manager:

[public get tailsFileService() {](https://github.com/rngadam/credo-ts/blob/a65a9c39879e83975de25022bd962a9ed16bcec3/packages/anoncreds/src/AnonCredsModuleConfig.ts#L82-L84)

https://github.com/rngadam/credo-ts/blob/a65a9c39879e83975de25022bd962a9ed16bcec3/packages/anoncreds/src/AnonCredsModuleConfig.ts#L82-L84

### FileSystem interface

https://github.com/rngadam/credo-ts/blob/a65a9c39879e83975de25022bd962a9ed16bcec3/packages/core/src/storage/FileSystem.ts#L7-L20

implementations:

* Node: https://github.com/rngadam/credo-ts/blob/755f5b8e546a769e9f4229f0281033da3e85ec04/packages/node/src/NodeFileSystem.ts
* React-native: https://github.com/rngadam/credo-ts/blob/755f5b8e546a769e9f4229f0281033da3e85ec04/packages/react-native/src/ReactNativeFileSystem.ts

### ReactNativeFileSystem

https://github.com/rngadam/credo-ts/blob/a65a9c39879e83975de25022bd962a9ed16bcec3/packages/react-native/src/ReactNativeFileSystem.ts#L27-L36

### RNFS aka react-native-fs.CachesDirectoryPath

https://www.npmjs.com/package/@dr.pogodin/react-native-fs#cachesdirectorypath

* Android:

https://github.com/birdofpreyru/react-native-fs/blob/eede7c9e0e7b02ab2952d584e0d54ee897d71d3f/android/src/main/java/com/drpogodin/reactnativefs/ReactNativeFsModule.kt#L76

* iOS

https://github.com/birdofpreyru/react-native-fs/blob/eede7c9e0e7b02ab2952d584e0d54ee897d71d3f/ios/ReactNativeFs.mm#L1064

### Android

https://developer.android.com/training/data-storage/app-specific#internal-create-cache

### iOS



