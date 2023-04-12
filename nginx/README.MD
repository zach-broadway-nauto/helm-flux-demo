# Helm Chart Files
These files support our kubernetes training and will do a basic install of an nginx server to demonstrate the usage of helm.

## Install/Upgrade Command:
```shell
helm upgrade --install --create-namespace --namespace nginx-helm nginx-rel . -f values.yaml
```

## Template Command:
The Template command will output yaml manifest files filled out
```shell
helm template --namespace nginx-helm -f values.yaml nginx-rel . --output-dir ./test
```
The Template command will output yaml manifest files filled out

* The -f specifies the values.yaml files to use. 
* "nginx-rel" is the release name. This specifies all of the values for the yaml names when creating the resource.
* You can use the --dry-run flag to test the install before actually running it.
* The `--create-namespace --namespace` command allows us to specify where to install/upgrade. It will create the namespace if it does not exist.
* To remove the deployment, use helm delete <release name>

## Helm check releases:
`helm ls --namespace=nginx-helm`

Check Upgrade & rollback histroy:
`helm history --namespace nginx-helm nginx-rel`

## Helm Rollback:
Rollback to previous release:
`helm rollback --namespace nginx-helm nginx-rel`

Rollback to specific releaseL
`helm rollback --namespace nginx-helm nginx-rel 2`
Note: You can also rollback forward, so from 2 to 6 for example.

