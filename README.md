# [RebornBuddy.Assemblies][0]

[0]: https://github.com/TheManta/RebornBuddy.Assemblies

[![Build Status][1]][2]
[![Download][3]][4]

[1]: https://github.com/TheManta/RebornBuddy.Assemblies/workflows/Publish/badge.svg
[2]: https://github.com/TheManta/RebornBuddy.Assemblies/actions "Build Status"
[3]: https://img.shields.io/badge/-DOWNLOAD-success
[4]: https://github.com/TheManta/RebornBuddy.Assemblies/packages "Download"

**RebornBuddy.Assemblies** is a NuGet package release of key [Reborn Buddy][5] assemblies, stripped of their code to function only as reference assemblies.  This simplifies third party development and automated builds by allowing the use of package managers instead of committing complete (and probably outdated) assemblies directly to repo.

These assemblies have been stripped of their code, leaving only the API behind -- **they cannot be executed**.  This project is only for third party developer convenience, not end users.  Please support the official release on the [Reborn Buddy][5] website.

[5]: https://www.rebornbuddy.com/ "Reborn Buddy"

## Usage

To use this package,

  1. Enable the custom GitHub Packages source.
  2. Install the package for your project.

### Enabling Package Source

GitHub Packages requires authentication, even for read-only access to public packages.  Instead of using your GitHub password, NuGet can accept and encrypt a read-only token for security purposes.

On GitHub,

  1. Visit then [Personal Access Tokens][6] page.
  2. Click "Generate New Token" in the top right.
  3. Set `Note` to "GitHub Packages Read-Only"
  4. Select scopes:
     * `repo`
     * `read:packages`

![Scopes][7]

  5. Click "Generate Token" at the bottom.
  6. Copy the new token.

[6]: https://github.com/settings/tokens "Personal Access Tokens"
[7]: https://i.imgur.com/F6T8hI2.png "Example"


In Visual Studio,

  1. Open Tools > NuGet Package Manager > Package Manager Console
  2. In the PM Console, run the following command after editing username and password:
  ```powershell
  dotnet nuget add source "https://nuget.pkg.github.com/TheManta/index.json" --name "GitHub/TheManta" --username "GITHUB_USER_HERE" --password "GITHUB_TOKEN_HERE"
  ```

### Installing the Package

In Visual Studio,

  1. Open Tools > NuGet Package Manager > Package Manager Console
  2. In the PM Console, run the following command after editing the project name:
  ```powershell
  Install-Package "RebornBuddy.Assemblies" -Source "GitHub/TheManta" -Project "YOUR_PROJECT_HERE"
  ```

To prevent the reference assemblies from being unnecessarily copied to the output folder on build,

  1. In the Solution Explorer, browse to the project's references.
  2. Set `Copy Local: False` for these references:
     * GreyMagic
     * RebornBuddy

Reborn Buddy will locate and load the full versions on its own.  Nothing from this package needs to be distributed with your addon.
