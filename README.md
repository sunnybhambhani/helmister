![Helmister](images/logo.png)

Helmister
--------------------------

This is a small bash utility which can help to install and uninstall multiple helm charts in one go.

Motive
--------------------------

Why I thought to write a simple bash utility?

- In some of the air-gapped environments it is sometimes a bit difficult to use the tools/utilities available because moving things inside an air-gapped environment is a challenge.
- Some of the environments are so secure that one may need to follow a whole process of getting all the security clearances and approval before using a tool/utility, which is all together a nightmare.
- I chose bash, the reason being it is pretty common among engineers and it is easily understandable.
- Plus I chose to have the script/utility source code open so that anyone can copy it, and tweak it based on their requirements.
- In future, I am planning to some more functionalities to this.

Usage
--------------------------

./helmister [OPTIONS]

Options
--------------------------

#### install

Install multiple helm charts in one go. Just need to have values.yaml file with what all charts needs to be installed. For more information around values.yaml, sample file is a part of base folder.

#### uninstall

Uninstall multiple helm charts in one go, this command too will consume the same values.yaml.

#### help

Display help.

Sample values.yaml
--------------------------

```
dry_run: false
create_namespace: false
wait: false
timeout: false # Defaults to 20mins
charts:
  - release_name: nginx2
    chart_name: nginx
    chart_repo: oci://registry-1.docker.io/bitnamicharts
    values_file: values/nginx-values.yaml
    version: 15.4.5
    namespace: default
```

Note
--------------------------

- Charts is an array, it can contain as many releases as you want.
- Helmister also support https:// registries.
- All the key value pairs under charts are mandatory except version and namespace,
  If not provided it will consider latest chart and default namespace respectively.

Dependencies
--------------------------

- cowsay
