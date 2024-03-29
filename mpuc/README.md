## Modpack Update Checker
This is the folder used by **Modpack Update Checker**
It contains metadata to keep track of the modpacks versions

This document serves as a guide for updating the modpack (there are a few config files to change and its easy to forget)

### Update Guide
To update the modpack, before exporting your client, there are 2 mods that manage modpack versions you need to change client configs for. *(any file paths mentioned in this section are within your Minecraft profiles root directory)*

* Modpack Update Checker
* * Edit `currentVersion` inside `/config/modpack-update-checker/config.json` to the modpacks new version (e.g `modpackVersion = "1.1.0"`)
* Better Compatability Checker:
* * Edit: `modpackVersion` inside `/config/bcc-common.toml` to be the modpacks new version (e.g `modpackVersion = "1.1.0"`)

You can now export the .mrpack file for the client modpack. Upload it to your file host of choice and hold onto the link.

### Update Modpack Repo
On the modpacks repository, modify meta.json with a new entry in the `versions` table.
```json
{
    "id": "1.1.0", // Your new version
    "releasedAt": 1711683206, // A unix timestamp for when it was released
    "promotions": {
        "downloads": {
            "generic": "https://files.com/modpack-1-1-0.mrpack" // The link for where it was uploaded
        }
    }
}
```
Next, create a folder inside the `versions` folder with the same name as your new version number (e.g `1.0.0`)
Once done, create a file inside that new folder called `changelog.txt` and write a description of whats new in this version. The contents of this text file will be displayed on modpack users clients when prompted to update to the new version, so make it descriptive!

The file structure should look like this:
```json
mpuc
│   meta.json
│   README.md
└───versions
    ├───1.0.2
    │       changelog.txt
    └───1.1.0 // New version we created
            changelog.txt // Changelog file with our update description
```