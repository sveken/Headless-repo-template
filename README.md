# Headless repo template
Template showing the file structure for using repo sync inside [VoxelBones Resonite Headless docker image](https://github.com/voxelbonecloud/headless-docker)

You may use this repo to for testing or a template. The config file found inside config will load an empty gridspace world without logging in.

## Important Note
Majority of configs will contain passwords to log in. It is therfore important to make your repo private, limit access to trusted users, or even self host your repo.

The container has a variable to enable access to private repos by using a generated user access token. 

Githubs documentation on user access tokens can be [found here](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens)

## Configuration
The following container variables configure this feature.

`ENABLE_GITPULL_CONFIG`= Setting this to true will make git clone/pull the repository to the staging directory and copy any .json files inside the [config](config) folder to /Config inside the container.

`ENABLE_GITPULL_MODS`= Setting this to true will make git clone/pull the repository to the staging directory. Next the container will copy the files inside the [rml_lib](rml_libs) [rml_mods](rml_mods) and [rml_config](rml_config) to the required directories inside the headless installation. **NOTE:** This also requires `ENABLE_MODS` to be true.

`REPO_URL`= The URL of the repository. Example https://github.com/sveken/Headless-repo-template

`REPO_IS_PRIVATE`= This changes the git commands to use authentication via an access token. Required for private repositories and highly recommended for configs with passwords. 

`REPO_ACCESS_TOKEN`= The access token for the repo if `REPO_IS_PRIVATE` is true

`KEEP_IN_SYNC`= If set to true this will wipe the /Config directory, rml_mods and rml_config inside the container before updating the directories from the repo. This clears any untracked files that may have been added directly to these directories on the host, Ensuring they stay in sync with what is downloaded from git.