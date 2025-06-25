# ASTRONEER Simplified Chinese to Traditional Chinese Localization Guide

Last Updated: June 25, 2025

## Overview

This guide provides detailed instructions for converting ASTRONEER's Simplified Chinese (zh-Hans) localization to Traditional Chinese (zh-HK). The process involves extracting game files, modifying localization resources, and creating a custom language pack.

## Prerequisites

- ASTRONEER game installation
- Required Tools:
  - [QuickBMS](https://aluigi.altervista.org/papers/quickbms.zip)
  - [Unreal Tournament 4 BMS Script](https://aluigi.altervista.org/bms/unreal_tournament_4.bms)
  - [UnrealLocresEditor v1.4.1](https://github.com/Snoozeds/UnrealLocresEditor/releases/download/1.4.1/UnrealLocresEditor-1.4.1-win-x64.zip)
  - [UnrealPak Utility](https://github.com/RiotOreO/unrealpak/archive/refs/heads/main.zip)

## Installation

1. Download the latest version of `zzz_ASTRONEER_zh-HK_p.pak`
2. Place the file in your ASTRONEER installation directory:

   ```
   [GAME_INSTALL_LOCATION]\ASTRONEER\
   ```

## Development Guide

### 1. Extracting Game Files

1. Extract QuickBMS to a local directory
2. Launch `quickbms_4gb_files.exe`
3. Select the BMS script: `unreal_tournament_4.bms`
4. When prompted, select the game PAK file:

   ```
   [GAME_INSTALL_LOCATION]\ASTRONEER\Astro\Content\Paks\Astro-WindowsNoEditor.pak
   ```

5. Choose an extraction directory (referred to as [TEMP])

### 2. Localization Process

#### 2.1 Engine Localization

1. Install UnrealLocresEditor v1.4.1
2. Launch `UnrealLocresEditor.Desktop.exe`
3. Confirm the download of `UnrealLocres.exe` when prompted
4. Open the Engine localization file:

   ```
   [TEMP]\Engine\Content\Localization\Engine\zh-Hans\Engine.locres
   ```

5. Perform the translation
6. Export the modified locres file to:

   ```
   zzz_[MOD_NAME]_p\Astro\Content\Localization\Game\zh-Hans\Engine.locres
   ```

#### 2.2 Game Localization

1. Repeat the process for Game.locres
2. Open source file:

   ```
   [TEMP]\mod\Engine\Content\Localization\Engine\zh-Hans\Game.locres
   ```

3. Export to:

   ```
   zzz_[MOD_NAME]_p\Engine\Content\Localization\Engine\zh-Hans\Engine.locres
   ```

### 3. File Structure

Ensure your mod directory follows this exact structure:

```
zzz_[MOD_NAME]_p/
├── Astro/
│   └── Content/
│       └── Localization/
│           └── Game/
│               └── zh-Hans/
│                   └── Game.locres
└── Engine/
    └── Content/
        └── Localization/
            └── Engine/
                └── zh-Hans/
                    └── Engine.locres
```

### 4. Creating the PAK File

1. Extract the UnrealPak utility
2. Open Command Prompt
3. Execute the following command:

   ```bash
   "[UNREALPAK_LOCATION]\unrealpak-main\UnrealPak.exe" "[MOD_LOCATION]\zzz_[MOD_NAME]_p.pak" -create=filelist.txt -compress
   ```

## Troubleshooting

- If QuickBMS fails to extract files, ensure you have sufficient disk space and appropriate permissions
- For UnrealLocresEditor issues, verify you have the latest .NET runtime installed
- If the PAK file doesn't load in-game, check file naming and directory structure

## Technical Notes

- File naming is critical:
  - The `_p` suffix indicates it's a patch file
  - The `zzz_` prefix ensures the game loads this PAK file last in the loading order, which is necessary for proper mod functionality
- Maintain original file structure within the PAK file
- Use appropriate character encoding (UTF-8) when editing localization files

## Version Compatibility

This guide is tested with:

- ASTRONEER v1.32.19.0
- UnrealLocresEditor v1.4.1
- QuickBMS v0.12
