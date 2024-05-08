# barrys_conda_envs

This is a collection of conda environments that I use on my MacBook
laptop and across various linux servers.  This is mostly for backup
and archive for my own use, but also for sharing with colleagues.  If
you've stumbled across them you are welcome use them if they are
useful to you.

## Conda snippets

The commands below are of course widely available with a Google
search, but for quick reference, a few conda commands that I use
frequently or are relevant to maintaining and using this repository
are listed below:

### Create conda environment YAML files

The first `env export` command below exports the full environment with
versions for all packages.  This allow for creating a more
repeatable/identical environment and might be preffered for tested
production environments.  The second `env export --from-history` only
includes the packages explicitly installed by the user and usually
doesn't include versions or dependencies.  This is a bit more flexible
and exportable because captures the 'gist' of a given environment
while allowing the conda environment created from this YAML file to
manage dependencies in a platform specific way.  This is probably the
way to go for development environments.

If you're not sure, use the 'from-history' as a starting point and
reflex to the fully explicit file if needed.

In the commands below, replace `environment` with the name of the base
name of environment you want to create or install.

```
conda list --explicit > environment_spec-file.txt
conda env export > ~/barrys_conda_envs/MacBook/envs/environment.yml
conda env export --from-history > ~/barrys_conda_envs/MacBook/envs/environment_from-history.yml
```



### Create a new conda environment from a YAML file

```
conda env create -f environment.yml
```

