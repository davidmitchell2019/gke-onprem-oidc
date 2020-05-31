* We used Packet.com for our Windows server deployment.
* We setup a domain controller using a custom domain and pointed DNS (Goddady A record) to the ADFS server.

* We used this article for ADFS setup:
https://www.virtuallyboring.com/how-to-setup-microsoft-active-directory-federation-services-adfs/

* We used Certify the web for SSL certification setup
https://certifytheweb.com/

* We used this article for OIDC setup:

https://cloud.google.com/anthos/gke/docs/on-prem/how-to/oidc-adfs

https://cloud.google.com/anthos/gke/docs/on-prem/how-to/oidc-adfs#mapping_ldap_attributes_to_claim_names

With 3 claim issuance parties:

|      LDAP attribute             | Outgoing claim  type     |
| Token groups (Unqualified names)| Group                    |
| User principle name             | Email address            |
| Sam account name                | Username                 |

* Our OIDC configuration file can be found in this repo under:

oidc-config.yaml.example

* This needs to be added to the user cluster yaml file.

Useful commands:

gkectl create-login-config --kubeconfig [USER_CLUSTER_KUBECONFIG]
Distribute and put in the right location as per documentation.

gcloud components install anthos-auth

gcloud anthos auth login --cluster nhsy-user-cluster-3

We used this for reading kubectl access tokens:

https://jwt.io/
