**List all environments**

```bash
conda env list
conda info --envs
```

**Create environment**

```bash
# create named environment
conda create --name myenv

# To create an environment with a specific version of Python
conda create -n myenv python=3.9
```

```bash
# Specifying a location for an environment
conda create --prefix ./ml_ds_env pandas
```

**Cloning an environment**

```bash
conda create --name myclone --clone myenv
```

**Activate environment**

```bash
# activate named environment
conda activate myenv

# activate custom location environment
conda activate ./ml_ds_env
```

**Deactivating an environment**

```bash
conda deactivate
```

**Viewing a list of the packages in an environment**

```bash
# see packages of current active environment
conda list

# see packages of other environments
conda list -n myenv
```

**Installing package**

```bash
conda install jupyter numpy
```

**Removing an environment**

```bash
conda remove --name myenv --all
```
