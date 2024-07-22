# Headless repo template
Template showing the file structure for using repo sync inside [VoxelBones Resonite Headless docker image](https://github.com/voxelbonecloud/headless-docker)

You may use this repo to for testing or a template. The config file found inside config will load an empty gridspace world without logging in.

## Important Note
Majority of configs will contain passwords to log in. It is therfore important to make your repo private, limit access to trusted users, or even self host your repo.

The container has a variable to enable access to private repos by using a generated user access token. 

Githubs documentation on user access tokens can be [found here](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens)
## What Happens
.json files in the config directory will be copied to /Config

Mod files inside the respective rml_ folders will be copied into the corresponding folder. ENABLE_MODS must also be true for this step.

