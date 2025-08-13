**Date:** August 12, 2025 

# NOTES

[Back to Exercise](./README.md) · [All Exercises](../../README.md#exercises)

- **Helm** is a package manager, and a **chart** is a packaging format that describes a set of related K8s resources[<sup>[1]</sup>](https://helm.sh/docs/topics/charts/#:~:text=Helm%20uses%20a,and%20so%20on.)
- A Helm **repository** is a hub where charts are stored, such as *Docker Hub* is for *Docker* images[<sup>[2]</sup>](https://artifacthub.io/packages/search?kind=0)
- Initializing a sample chart repository[<sup>[3]</sup>](https://helm.sh/docs/intro/quickstart/)
  ```bash
  helm repo add [NAME] [URL] [flags]
  ```
  e.g.,
  ```bash
  helm repo add bitnami https://charts.bitnami.com/bitnami
  ```
- searching for a repository
  ```bash
  helm search SOURCE REPOSITORY
  ```
  e.g.,
  ```bash
  helm search repo bitnami
  ```

> [!NOTE]
> Helm can search two different sources; hub (Artifact Hub), and repo (local machine).[<sup>[6]</sup>](https://helm.sh/docs/intro/using_helm/#customizing-the-chart-before-installing:~:text=helm%20search%20hub,connection%20is%20needed.)

- searching for a repository chart
  ```bash
  helm search SOURCE REPOSITORY/CHART
  ```
  e.g.,
  ```bash
  helm search repo bitnami/mysql
  ```
  ```bash
  helm search hub bitnami/mysql
  ```

- reading about the features of a helm chart
  ```bash
  helm show chart REPOSITORY/CHART
  ```
  e.g.,
  ```bash
  helm show chart bitnami/mysql
  ```
- reading the detailed documentation of a helm chart
  ```bash
  helm show all REPOSITORY/CHART
  ```
  e.g.,
  ```bash
  helm show all bitnami/mysql
  ```
- updating repositories to get the latest charts
  ```bash
  helm repo update
  ```
- A **release** is a running instance of a Helm chart or a deployment[<sup>[4]</sup>](https://helm.sh/docs/intro/using_helm/#customizing-the-chart-before-installing:~:text=A%20Release%20is%20an%20instance%20of%20a%20chart%20running%20in%20a%20Kubernetes%20cluster.)
- installing a particular chart
  ```bash
  helm install REPOSITORY/CHART --generate-name
  ```
  e.g.,
  ```bash
  helm install bitnami/mysql --generate-name
  ```
- uninstalling a particular release
  ```bash
  helm uninstall RELEASE
  ```
  e.g.,
  ```bash
  helm unistall mysql-1755029039
  ```

> [!NOTE]
> `--generate-name` is important.


- seeing the list of deployed resources, also known as **releases**.
  ```bash
  helm list
  ```
- reading the status of a release
  ```bash
  helm status RELEASE
  ```
  e.g.,
  ```bash
  helm status mysql-1755029039
  ```
- keeping history of a release despite deleting it
  ```bash
  helm uninstall RELEASE --keep-history
  ```
  e.g.,
  ```bash
  helm uninstall mysql-1755029039 --keep-history
  ```

> [!NOTE]
> Helm keeps track of releases if they are deleted using `--keep-history` option.[<sup>[4]</sup>](https://helm.sh/docs/intro/using_helm/#:~:text=If%20you%20wish%20to%20keep%20a%20deletion%20release%20record%2C%20use%20helm%20uninstall%20%2D%2Dkeep%2Dhistory)


- downloading a chart from a repository without installing it
  ```bash
  helm pull REPOSITORY/CHART
  ```
  e.g.,
  ```bash
  helm pull bitnami/mysql
  ```

> [!IMPORTANT]
> Downloading the image results in a `.tgz` file. Be sure to rename it `tar.gz`, and then unzip/extract it to get the Helm chart.
>
>```bash
>mv SOURCE TARGET
>tar -xvzf TARGET
>```
>e.g.,
>```bash
>mv wordpress-25.0.8.tgz wordpress-25.0.8.tar.gz
>tar -xvzf wordpress-25.0.8.tar.gz
>```

- following is the Bitnami Wordpress Helm chart structure
  ```bash
  ├───charts                          # Subcharts used by the main WordPress chart (dependencies)
  │   ├───common                      # Common templates and helpers shared across Bitnami charts
  │   │   └───templates
  │   │       └───validations         # Validation templates (e.g., schema validation)
  │   │
  │   ├───mariadb                     # Subchart for MariaDB (used as the WordPress database)
  │   │   ├───charts
  │   │   │   └───common              # Common chart dependencies for MariaDB (reuses Bitnami common)
  │   │   │       └───templates
  │   │   │           └───validations # Validation templates for the common library
  │   │   └───templates               # Main template files for deploying MariaDB
  │   │       ├───primary             # Templates specific to the primary MariaDB instance
  │   │       ├───secondary           # Templates for the secondary (replica) instances
  │   │       └───update-password     # Templates to handle password rotation/update
  │   │
  │   └───memcached                   # Subchart for Memcached (used for object caching in WordPress)
  │       ├───charts
  │       │   └───common              # Common library chart reused by Memcached
  │       │       └───templates
  │       │           └───validations # Validation templates for Memcached common chart
  │       └───templates               # Templates specific to the Memcached deployment
  │
  └───templates                       # Top-level templates for the WordPress chart itself
  ```

> [!TIP]
> Helm installs charts into Kubernetes, creating a new release for each installation. And to find new charts, you can search Helm chart repositories.[<sup>[5]</sup>]((https://helm.sh/docs/intro/using_helm/#customizing-the-chart-before-installing:~:text=Helm%20installs%20charts%20into%20Kubernetes%2C%20creating%20a%20new%20release%20for%20each%20installation.%20And%20to%20find%20new%20charts%2C%20you%20can%20search%20Helm%20chart%20repositories.))

- reading the default configuration values of a chart
  ```bash
  helm show values REPOSITORY/CHART
  ```
  e.g.,
  ```bash
  helm show values bitnami/wordpress
  ```

## References

1. [Helm Charts Documentation](https://helm.sh/docs/topics/charts/)
2. [Artifact Hub](https://artifacthub.io/packages/search?kind=0)
3. [Helm Quick Start](https://helm.sh/docs/intro/quickstart/)
4. [Customizing the Chart before installing](https://helm.sh/docs/intro/using_helm/#customizing-the-chart-before-installing)
