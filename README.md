<div align="center">

# 🔄 SimpleDevelopments Version Hub

### Centralized version metadata and changelog hosting for SimpleDevelopments resources.

<p>
  <a href="https://simpledevelopments.org/store">
    <img src="https://img.shields.io/badge/Explore_Our_Store-5865F2?style=for-the-badge&logo=googlechrome&logoColor=white" />
  </a>
  <a href="https://discord.gg/RquDVTfDwu">
    <img src="https://img.shields.io/badge/Join_Our_Discord-5865F2?style=for-the-badge&logo=discord&logoColor=white" />
  </a>
  <a href="https://github.com/Fadinlaws123/ScriptVersionChecker">
    <img src="https://img.shields.io/badge/View_on_GitHub-181717?style=for-the-badge&logo=github&logoColor=white" />
  </a>
</p>

<p>
  <img src="https://img.shields.io/badge/Purpose-Version_Metadata-238636?style=flat-square" />
  <img src="https://img.shields.io/badge/Format-JSON-000000?style=flat-square&logo=json&logoColor=white" />
  <img src="https://img.shields.io/badge/Status-Active-238636?style=flat-square" />
  <img src="https://img.shields.io/github/stars/Fadinlaws123/ScriptVersionChecker?style=flat-square&logo=github&label=Stars" />
</p>

</div>

---

## 📖 About

This repository acts as the central **version metadata hub** for SimpleDevelopments resources.

Individual scripts can check their corresponding file in this repository to determine whether a newer version is available. Each version file can provide the latest release number, download location, and changelog history without requiring that information to be hardcoded directly into the resource.

This repository is primarily intended to support SimpleDevelopments scripts and their built-in version checking systems rather than function as a standalone FiveM resource.

---

## ✨ What It Provides

- Centralized version information for SimpleDevelopments resources
- Latest-version tracking
- Direct download or release links
- Per-version changelog history
- Lightweight JSON-based metadata
- Easy integration with Lua or JavaScript version checkers
- A single location for maintaining update information across multiple projects

---

## ⚙️ How It Works

Each supported resource has its own metadata file stored in this repository.

A script's version checker requests the corresponding file, compares the installed version against `latest_version`, and can then notify the server owner when an update is available.

A typical version file looks like this:

```json
{
  "latest_version": "1.2",
  "download_url": "https://github.com/YourName/YourResource/releases",
  "changelog": [
    {
      "version": "1.2",
      "date": "2026-06-30",
      "changes": [
        "Added a new feature.",
        "Fixed an existing issue."
      ]
    }
  ]
}
```

---

## 📋 Metadata Structure

| Field | Description |
| --- | --- |
| `latest_version` | The newest publicly available version of the resource. |
| `download_url` | The location users should visit to download the latest release. |
| `changelog` | A list containing current and previous version history. |
| `version` | The version number associated with a changelog entry. |
| `date` | The release date for that version. |
| `changes` | A list of changes, fixes, or additions included in the release. |

---

## 🔌 Example Integration

A FiveM resource can retrieve its metadata file using `PerformHttpRequest` and compare the returned version against its installed version.

```lua
PerformHttpRequest(versionFileUrl, function(statusCode, response)
    if statusCode ~= 200 then
        print('Unable to check for updates.')
        return
    end

    local data = json.decode(response)

    if data and data.latest_version then
        print(('Latest version: %s'):format(data.latest_version))
    end
end, 'GET')
```

The exact implementation may vary between resources depending on how version comparisons, changelogs, and console output are handled.

---

## 🗂️ Repository Usage

This repository contains version files for multiple SimpleDevelopments projects. Resource repositories can reference their matching metadata file through GitHub's raw content URL.

When a new resource version is released, its metadata file should be updated with:

1. The new `latest_version`
2. The current download or release URL
3. A new changelog entry

Keeping this information centralized allows existing installations to detect updates without requiring a separate service or database.

---

## 📋 Requirements

- A resource with an HTTP-capable version checker
- Access to the corresponding raw metadata file
- No database required
- No external API service required

---

## 🛠️ Notes

This repository is infrastructure for SimpleDevelopments projects. Most users will never need to install or download it directly.

If a version check fails, the resource itself should continue running normally and treat update checking as an optional convenience rather than a hard dependency.

---

## 🌐 SimpleDevelopments

This version hub is maintained by **SimpleDevelopments** and supports update checking across our FiveM resources and other projects.

SimpleDevelopments creates FiveM scripts, Discord bots, custom development, liveries, vehicles, and other community resources.

---

<div align="center">

### Keep it Simple. Keep it SimpleDevelopments.

⭐ **Used by SimpleDevelopments resources to keep updates simple and centralized.**

</div>
