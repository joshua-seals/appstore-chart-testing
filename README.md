# appstore

![Version: 5.2.0](https://img.shields.io/badge/Version-5.2.0-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 2.0.0](https://img.shields.io/badge/AppVersion-2.0.0-informational?style=flat-square)

A Helm chart for Kubernetes

## Requirements

| Repository | Name | Version |
|------------|------|---------|
| https://charts.bitnami.com/bitnami | postgresql | 11.6.26 |

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| ACCOUNT_DEFAULT_HTTP_PROTOCOL | string | `"http"` | Choose http or https for the protocol that is used by external users to access the appstore web service. |
| SET_BUILD_ENV_FROM_FILE | bool | `false` | Set environment variables from a file. |
| affinity | object | `{}` |  |
| ambassador.flag | bool | `true` | register appstore with ambassador flag: <True or False> |
| appStorage.claimName | string | `nil` |  |
| appStorage.existingClaim | bool | `false` |  |
| appStorage.storageClass | string | `nil` |  |
| appStorage.storageSize | string | `"2Gi"` |  |
| apps.DATASOURCE_CONNECTION_URL | string | `""` |  |
| apps.DATASOURCE_PASSWORD | string | `""` |  |
| apps.DATASOURCE_USERNAME | string | `"ohdsi"` |  |
| apps.DICOMGH_GOOGLE_CLIENT_ID | string | `""` |  |
| apps.FLYWAY_DATASOURCE_CONNECTION_URL | string | `""` |  |
| apps.FLYWAY_DATASOURCE_PASSWORD | string | `""` |  |
| apps.FLYWAY_DATASOURCE_USERNAME | string | `"ohdsi"` |  |
| apps.HELX_DB_HOSTNAME | string | `""` | Specify the database hostname used for pgAdmin's clients to connect to. If specified this replaces 'mimic-postgresql' in the pgadmin4.db configuration file. |
| apps.PGADMIN_EMAIL | string | `"user@domain.com"` | Specify email for pgAdmin user. |
| apps.WEBTOP_PGID | string | `"1000"` | PGID variable in webtop specifies the GID to switch the user to after initialization. |
| apps.WEBTOP_PUID | string | `"1000"` | PUID variable in webtop specifies the UID to switch the user to after initialization. |
| appstoreEntrypointArgs | string | `"make start"` | Allow for a custom entrypoint command via the values file. |
| artillery.loadArrivalRate | int | `10` |  |
| artillery.loadDuration | int | `10` |  |
| artillery.loadTest | bool | `false` |  |
| artillery.smokeTest | bool | `false` | When either smokeTest or loadTest is true, set CREATE_TEST_USERS, TEST_USERS_PATH under django settings. |
| db | object | `{"host":"postgresql","name":"appstore","port":5432}` | appstore database settings |
| debug | string | `""` |  |
| django.ALLOW_DJANGO_LOGIN | string | `""` | show Django log in fields (true | false) |
| django.ALLOW_SAML_LOGIN | string | `""` | show SAML log in fields (true | false) |
| django.APPSTORE_DJANGO_PASSWORD | string | `""` |  |
| django.APPSTORE_DJANGO_USERNAME | string | `"admin"` |  |
| django.AUTHORIZED_USERS | string | `""` | user emails for oauth providers |
| django.CREATE_TEST_USERS | string | `"false"` | create test users for load testing |
| django.DEV_PHASE | string | `"live"` | should be 'live' unless you are doing some kind of development |
| django.DOCKSTORE_APPS_BRANCH | string | `"v1.6.0"` | Specify the git branch to use for HeLx app specifications.  When declaring 'tycho.externalAppRegistryRepo' leave this as an empty string. |
| django.EMAIL_HOST_PASSWORD | string | `""` | password of account to use for outgoing emails |
| django.EMAIL_HOST_USER | string | `""` | email of account to use for outgoing emails |
| django.IMAGE_DOWNLOAD_URL | string | `""` | Specify URL to use for the "Image Download" link on the top part of website. |
| django.RECIPIENT_EMAILS | string | `""` | list of appstore registration emails |
| django.REMOVE_AUTHORIZED_USERS | string | `""` | user emails to remove from an already-existing database |
| django.SESSION_IDLE_TIMEOUT | int | `3600` | idle timeout for user web session |
| django.TEST_USERS_PATH | string | `"/usr/src/inst-mgmt/artillery-tests/payloads"` | parent directory where the users.txt would be mounted |
| django.TEST_USERS_SECRET | string | `"test-users-secret"` | secret file deployed on the cluster to fetch the test users |
| djangoSettings | string | `"helx"` | set the theme for appstore (bdc, braini, restartr, scidas) |
| extraEnv | object | `{}` |  |
| fetcherImage.pullPolicy | string | `"IfNotPresent"` | pull policy |
| fetcherImage.repository | string | `"helxplatform/url-fetch"` | repository where image is located |
| fetcherImage.tag | string | `"latest"` |  |
| fullnameOverride | string | `""` |  |
| global.ambassador_id | string | `nil` | specify the id of the ambassador for Tycho-launched services. |
| global.stdnfsPvc | string | `"stdnfs"` | the name of the PVC to use for user's files |
| gunicorn.workers | int | `5` | Set the number of gunicorn workers.  (2*CPU)+1 is recommended. |
| helx_ui | object | `{"REACT_APP_ANALYTICS":"","REACT_APP_APPSTORE_ASSET_BRANCH":"master","REACT_APP_HELX_SEARCH_URL":"","REACT_APP_SEMANTIC_SEARCH_ENABLED":"false","REACT_APP_UI_BRAND_NAME":"","REACT_APP_WORKSPACES_ENABLED":"true"}` | Various settings for helx-ui which will get expressed as env variables in container |
| helx_ui.REACT_APP_ANALYTICS | string | `""` | REACT_APP_ANALYTICS (string) HeLx Mixpanel project analytics token |
| helx_ui.REACT_APP_APPSTORE_ASSET_BRANCH | string | `"master"` | REACT_APP_APPSTORE_ASSET_BRANCH: (string) branchname of appstore branch |
| helx_ui.REACT_APP_HELX_SEARCH_URL | string | `""` | REACT_APP_HELX_SEARCH_URL: (url)  URL of tranql |
| helx_ui.REACT_APP_SEMANTIC_SEARCH_ENABLED | string | `"false"` | REACT_APP_SEMANTIC_SEARCH_ENABLED: (boolean) Enable/Disable helx-ui search. |
| helx_ui.REACT_APP_UI_BRAND_NAME | string | `""` | REACT_APP_UI_BRAND_NAME: (string) defaults to the value of djangoSettings values: bdc, braini, eduhelx, eduhelx-chip690, eduhelx-sandbox, restartr, scidas, tracs |
| helx_ui.REACT_APP_WORKSPACES_ENABLED | string | `"true"` | REACT_APP_WORKSPACES_ENABLED: (boolean) Enable/Disable workspaces |
| image.pullPolicy | string | `"IfNotPresent"` | pull policy |
| image.repository | string | `"containers.renci.org/helxplatform/appstore"` | repository where image is located |
| image.tag | string | `nil` | Overrides the image tag whose default is the chart appVersion. Set to "" before release! |
| imagePullSecrets | list | `[]` | credentials for a private repo |
| irods.BRAINI_RODS | string | `""` |  |
| irods.IROD_APPROVED_USERS | string | `""` |  |
| irods.IROD_COLLECTIONS | string | `""` |  |
| irods.IROD_ZONE | string | `""` |  |
| irods.NRC_MICROSCOPY_IRODS | string | `""` |  |
| irods.RODS_PASSWORD | string | `""` |  |
| irods.RODS_USERNAME | string | `""` |  |
| irods.enabled | bool | `false` | enable irods support (true | false) |
| logLevel | string | `"WARNING"` | Set the log level for the application.  (DEBUG INFO WARNING ERROR CRITICAL) |
| nameOverride | string | `""` |  |
| networkPolicyLabels.role | string | `"appstore"` |  |
| nodeSelector | object | `{}` |  |
| oauth.GITHUB_CLIENT_ID | string | `""` |  |
| oauth.GITHUB_KEY | string | `""` |  |
| oauth.GITHUB_NAME | string | `""` |  |
| oauth.GITHUB_SECRET | string | `""` |  |
| oauth.GITHUB_SITES | string | `""` |  |
| oauth.GOOGLE_CLIENT_ID | string | `""` |  |
| oauth.GOOGLE_KEY | string | `""` |  |
| oauth.GOOGLE_NAME | string | `""` |  |
| oauth.GOOGLE_SECRET | string | `""` |  |
| oauth.GOOGLE_SITES | string | `""` |  |
| oauth.OAUTH_PROVIDERS | string | `""` | oauth providers separated by commas (google, github) |
| oauth.claimName | string | `"appstore-oauth-pvc"` |  |
| oauth.existingClaim | bool | `false` |  |
| oauth.storageClass | string | `nil` |  |
| podAnnotations | object | `{}` |  |
| postgresql | object | `{"audit":{"logConnections":true,"logHostname":true},"enabled":true,"global":{"postgresql":{"auth":{"database":"appstore-oauth","password":"renciAdmin","postgresPassword":"adminPass","username":"renci"}}},"networkPolicyEnabled":true,"persistence":{"existingClaim":"appstore-postgresql-pvc","storageClass":null},"primary":{"labels":{"np-label":"appstore-db"},"podLabels":{"np-label":"appstore-db"}},"volumePermissions":{"enabled":true}}` | postgresql settings |
| postgresql.audit | object | `{"logConnections":true,"logHostname":true}` | postgresql logs |
| postgresql.global.postgresql | object | `{"auth":{"database":"appstore-oauth","password":"renciAdmin","postgresPassword":"adminPass","username":"renci"}}` | postgresql credentials |
| postgresql.networkPolicyEnabled | bool | `true` | enable/disable postgresql network policy, allows traffic to and from appstore pod only. |
| postgresql.persistence | object | `{"existingClaim":"appstore-postgresql-pvc","storageClass":null}` | postgresql persistence storage |
| postgresql.primary | object | `{"labels":{"np-label":"appstore-db"},"podLabels":{"np-label":"appstore-db"}}` | postgresql labels |
| replicaCount | int | `1` |  |
| resources.limits.cpu | string | `"500m"` |  |
| resources.limits.memory | string | `"1024Mi"` |  |
| resources.requests.cpu | string | `"200m"` |  |
| resources.requests.memory | string | `"300Mi"` |  |
| saml.ASSERTION_URL | string | `""` |  |
| saml.AUTHORITY_URL | string | `""` |  |
| saml.ENTITY_ID | string | `""` |  |
| saml.cache.APPSTORE_DIRECTORY | string | `"/saml"` |  |
| saml.cache.APPSTORE_FILE | string | `"saml_metadata.xml"` |  |
| saml.cache.FETCH_FILE | string | `"/data/saml_metadata.xml"` |  |
| saml.cache.FETCH_INTERVAL | string | `"60000"` |  |
| saml.cache.claimName | string | `"saml-cache"` |  |
| saml.cache.enabled | bool | `false` |  |
| saml.cache.storageClass | string | `""` |  |
| saml.cache.storageSize | string | `"20M"` |  |
| security.isolatedApps | bool | `true` |  |
| securityContext.fsGroup | int | `0` |  |
| securityContext.runAsGroup | int | `0` |  |
| securityContext.runAsUser | int | `0` |  |
| service.name | string | `"http"` |  |
| service.port | int | `80` |  |
| service.type | string | `"ClusterIP"` |  |
| serviceAccount.create | bool | `true` | specifies whether a service account should be created |
| serviceAccount.name | string | `nil` | The name of the service account to use. If not set and create is true, a name is generated using the fullname template |
| tolerations | list | `[]` |  |
| tycho.createHomeDirs | bool | `true` | Create Home and shared directories for users. |
| tycho.enableInitContainer | bool | `true` | Start the init container to take care of any needed tasks before the main container is started.  This can be to create certain directories or set file permissions. |
| tycho.externalAppRegistryAppSpecsDir | string | `"app-specs"` |  |
| tycho.externalAppRegistryBranch | string | `nil` | The branch that would be appended to 'externalAppRegistryRepo' to retrieve the app registry and defaults files.  The full URL, if using the externalAppRegistryRepo example for the app registry file would be  'https://github.com/helxplatform/helx-apps/raw/master/app-registry.yaml'. The default value is the AppVersion of this chart prefixed with a 'v' (ex. v2.0.0). |
| tycho.externalAppRegistryEnabled | bool | `false` | Enable/disable the external app registry file for Tycho.  Set 'django.DOCKSTORE_APPS_BRANCH' to an empty string when when using an external app registry. |
| tycho.externalAppRegistryRepo | string | `"https://github.com/helxplatform/helx-apps/raw"` | Can be set to a git repo URL for fetching the app registry file or defaults file.  Something in the form of  'https://github.com/helxplatform/helx-apps/raw'. |
| tycho.fsGroup | int | `0` | Application processes launched will also be part of this supplimentary group. |
| tycho.init | object | `{"resources":{"cpus":"250m","memory":"250Mi"}}` | Resource for Tycho init container. Defaults cpus|250m memory|250Mi |
| tycho.initRunAsGroup | int | `0` | Init processes will have this group permissions. |
| tycho.initRunAsUser | int | `0` | Init processes will run as this user. |
| tycho.parent_dir | string | `"/home"` | directory that will be used to mount user's home directories in |
| tycho.runAsGroup | int | `0` | Application processes launched will have this group permissions. |
| tycho.runAsUser | int | `0` | Application processes launched will run as this user. |
| tycho.shared_dir | string | `"shared"` | name of directory to use for shared data |
| tycho.subpath_dir | string | `nil` | Name of directory to use for a user's home directory.  If null then the user's username will be used. |
| updateStrategy.type | string | `"Recreate"` | 'RollingUpdate' or 'Recreate'. Must use Recreate if mounting PVCs due to multi-attach errors. |
| useSparkServiceAccount | bool | `false` | Set to true, when using blackbalsam. |
| userStorage.createPVC | bool | `true` | Create a PVC for user's files.  If false then the PVC needs to be created outside of the appstore chart. |
| userStorage.nfs.createPV | bool | `false` |  |
| userStorage.nfs.path | string | `nil` |  |
| userStorage.nfs.server | string | `nil` |  |
| userStorage.storageClass | string | `nil` |  |
| userStorage.storageSize | string | `"10Gi"` |  |

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v1.11.0](https://github.com/norwoodj/helm-docs/releases/v1.11.0)
