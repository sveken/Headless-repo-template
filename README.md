# Headless repo template
Template showing the file structure for using repo sync inside [VoxelBones Resonite Headless docker image](https://github.com/voxelbonecloud/headless-docker)

You may use this repo for testing or a template. The config file found inside config will load an empty gridspace world without logging in.

## Important Note
Majority of configs will contain passwords to log in. It is therfore important to make your repo private, limit access to trusted users, or even self host your repo.

The container has a variable to enable access to private repos by using a generated personal user access token. 

You can test private repo access with git installed on your local machine by using `git clone https://git_username:your_personal_access_token@urltotherepo-removehttps`

example
`git clone https://sveken:superfancywzsedfgd@github.com/sveken/super-private-test-headless-repo`

Githubs documentation on user access tokens can be [found here](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens)

## Configuration
The following container variables configure this feature.

`ENABLE_GIT_CONFIG`= Setting this to true will make git clone/pull the repository to the staging directory and copy any .json files inside the [config](config) folder to /Config inside the container. **NOTE:** the /Config directly in your compose but not have `:ro` on the end, as this marks it as read only.

`ENABLE_GIT_MODS`= Setting this to true will make git clone/pull the repository to the staging directory. Next the container will copy the files inside the [rml_lib](rml_libs) [rml_mods](rml_mods) and [rml_config](rml_config) to the required directories inside the headless installation. **NOTE:** This also requires `ENABLE_MODS` to be true.

`GIT_URL`= The URL of the repository. Example https://github.com/sveken/Headless-repo-template

`GIT_REPOSITORY_PRIVATE`= This changes the git commands to use authentication via an access token. Required for private repositories and highly recommended for configs with passwords. 

`GIT_USERNAME`= Your git username for accessing the repo, used in conjuction with the Personal Token

`GIT_ACCESS_TOKEN`= The access token for the repo if `GIT_REPOSITORY_PRIVATE` is true. Needs to be a PAT and only read access is required. 

`KEEP_IN_SYNC`= If set to true this will wipe the /Config directory, rml_mods and rml_config inside the container before updating the directories from the repo. This clears any untracked files that may have been added directly to these directories on the host, Ensuring they stay in sync with what is downloaded from git.
