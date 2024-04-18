![Helmister](artifacts/images/logo.png)

Helmister
--------------------------

This is a small bash utility which can help to install and uninstall multiple helm charts in one go. The idea is inspired by `helmfile`.

Motive
--------------------------

- In some of the air-gapped environments it is sometimes a bit difficult to use the tools/utilities available because moving things inside an air-gapped environment is a challenge.
- Some of the environments are so secure that one may need to follow a whole process of getting all the security clearances and approval before using a tool/utility, which is all together a nightmare.
- I chose bash, the reason being it is pretty common among engineers and it is easily understandable.
- The source code can be found here: <https://github.com/sunnybhambhani/helmister>
- You can copy it, and tweak it based on your requirements.

Dependencies
--------------------------

- yq (required)
- cowsay (optional)

Usage
--------------------------

Options
--------------------------

#### install

Install multiple helm charts in one go. Just need to have config.yaml file with what all charts needs to be installed. For more information around config.yaml, sample file is a part of base folder.

#### uninstall

Uninstall multiple helm charts in one go, this command too will consume the same config.yaml.

#### help

Display help.

Sample config.yaml
--------------------------

```
dry_run: false
create_namespace: true
wait: false
timeout: false # If true, defaults to 20 mins
charts:
  - release_name: nginx
    chart_name: nginx
    chart_repo: oci://registry-1.docker.io/bitnamicharts
    values_file: values/nginx-values.yaml
  - release_name: argocd
    chart_name: argo-cd
    chart_repo: https://argoproj.github.io/argo-helm
    values_file: values/argo-cd.yaml
    version: 6.4.0
    namespace: argo-cd
```

Note
--------------------------

- Charts is an array, it can contain as many releases as you want.
- It also support both oci:// and https:// registries.
- All the key value pairs under charts are mandatory except version and namespace,
  - If not provided it will consider latest chart and default namespace respectively.
- Initial messages are printed using cowsay (It is not necessary though if required, get this installed using apt/yum/brew/dpkg based on your distribution).
