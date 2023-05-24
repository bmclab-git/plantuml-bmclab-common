# plantuml-bmclab-common

# Sprites for PlantUML

This repository includes a set of logos from [BMCLAB EcoSystem](https://cloudogu.com/?mtm_campaign=sprites&mtm_kwd=website&mtm_source=github&mtm_medium=link) Dogus and other tools for using as [Sprites](http://plantuml.com/sprite) in [PlantUML](http://plantuml.com). BTW: Check out our Git based wiki [Smeagol](https://github.com/cloudogu/smeagol) which has rich PlantUML support!

This work was inspired by [tupadr3/plantuml-icon-font-sprites](https://github.com/tupadr3/plantuml-icon-font-sprites). (Note: if you use their sprites in the same PlantUML diagram with sprites from this repo, you don't have to include the file common.puml from their repo. The code is already in common.puml of this repo.)

## Usage

First include the file common.puml either via path or url. It also contains style definitions according to the BMCLAB CI

```
[...]
!include ../common.puml
!includeurl https://raw.githubusercontent.com/bmclab-git/plantuml-bmclab-common/main/common.puml
[...]
```
You can define a macro for the URL

```
[...]
!define BMCLABURL https://raw.githubusercontent.com/bmclab-git/plantuml-bmclab-common/main
!includeurl BMCLABURL/common.puml
[...]
```

Then include the sprites that you want to use 

```
[...]
!includeurl BMCLABURL/dogus/scm.puml
!includeurl BMCLABURL/dogus/smeagol.puml
[...]
```

To use the Sprites you can include their name directly with <<$name>>

```
[...]
node "BMCLAB Ecosystem" <<$cloudogu>> {
[...]
```

or add one of the defined macros. Prefix can be either 'DOGU' or 'TOOL':

```
[...]
<prefix>_<name>(alias)
<prefix>_<name>(alias,label)
<prefix>_<name>(alias,label,shape)
<prefix>_<name>(alias,label,shape,color)
[...]
```

## Complete Example
```
@startuml
!define BMCLAB https://raw.githubusercontent.com/bmclab-git/plantuml-bmclab-common/main
!includeurl BMCLAB/common.puml
!includeurl BMCLAB/dogus/jenkins.puml
!includeurl BMCLAB/dogus/cloudogu.puml
!includeurl BMCLAB/dogus/scm.puml
!includeurl BMCLAB/dogus/smeagol.puml
!includeurl BMCLAB/dogus/nexus.puml
!includeurl BMCLAB/tools/k8s.puml

node "BMCLAB Ecosystem" <<$cloudogu>> {
	DOGU_JENKINS(jenkins, Jenkins) #ffffff
	DOGU_SCM(scm, SCM-Manager) #ffffff
	DOGU_SMEAGOL(smeagol, Smeagol) #ffffff
	DOGU_NEXUS(nexus,Nexus) #ffffff
}

TOOL_K8S(k8s, Kubernetes) #ffffff

actor developer

developer -> smeagol : "Edit Slides"
smeagol -> scm : Push
scm -> jenkins : Trigger
jenkins -> nexus : Deploy
jenkins -> k8s : Deploy

@enduml
```

![Example](example.png "Example")

## List of all Dogu Sprites

| Sprite | Dogu name | Macro | Name |
|--------|-----------|-------|------|
| ![CAS](https://raw.githubusercontent.com/bmclab-git/plantuml-bmclab-common/main/dogus/cas.jpg "CAS") | CAS | DOGU_CAS | $cas |
| ![Cloudogu](https://raw.githubusercontent.com/bmclab-git/plantuml-bmclab-common/main/dogus/cloudogu.jpg "Cloudogu") | Cloudogu | DOGU_CLOUDOGU | $cloudogu |
| ![Cockpit](https://raw.githubusercontent.com/bmclab-git/plantuml-bmclab-common/main/dogus/cockpit.png "Cockpit") | Cockpit | DOGU_COCKPIT | $cockpit |
| ![Jenkins](https://raw.githubusercontent.com/bmclab-git/plantuml-bmclab-common/main/dogus/jenkins.jpg "Jenkins") | Jenkins | DOGU_JENKINS | $jenkins |
| ![Nexus](https://raw.githubusercontent.com/bmclab-git/plantuml-bmclab-common/main/dogus/nexus.jpg "Nexus") | Nexus | DOGU_NEXUS | $nexus |
| ![Nginx](https://raw.githubusercontent.com/bmclab-git/plantuml-bmclab-common/main/dogus/nginx.jpg "Nginx") | Nginx | DOGU_NGINX | $nginx |
| ![OpenLDAP](https://raw.githubusercontent.com/bmclab-git/plantuml-bmclab-common/main/dogus/openldap.jpg "OpenLDAP") | OpenLDAP | DOGU_OPENLDAP | $openldap |
| ![PlantUML](https://raw.githubusercontent.com/bmclab-git/plantuml-bmclab-common/main/dogus/plantuml.jpg "PlantUML") | PlantUML | DOGU_PLANTUML | $plantuml |
| ![Postfix](https://raw.githubusercontent.com/bmclab-git/plantuml-bmclab-common/main/dogus/postfix.jpg "Postfix") | Postfix | DOGU_POSTFIX | $postfix |
| ![PostgreSQL](https://raw.githubusercontent.com/bmclab-git/plantuml-bmclab-common/main/dogus/postgresql.png "PostgreSQL") | PostgreSQL | DOGU_POSTGRESQL | $postgresql |
| ![Redmine](https://raw.githubusercontent.com/bmclab-git/plantuml-bmclab-common/main/dogus/redmine.jpg "Redmine") | Redmine | DOGU_REDMINE | $redmine |
| ![Registrator](https://raw.githubusercontent.com/bmclab-git/plantuml-bmclab-common/main/dogus/registrator.jpg "Registrator") | Registrator | DOGU_REGISTRATOR | $registrator |
| ![SCM Manager](https://raw.githubusercontent.com/bmclab-git/plantuml-bmclab-common/main/dogus/scm.jpg "SCM Manager") | SCM Manager | DOGU_SCM | $scm |
| ![Smeagol](https://raw.githubusercontent.com/bmclab-git/plantuml-bmclab-common/main/dogus/smeagol.png "Smeagol") | Smeagol | DOGU_SMEAGOL | $smeagol |
| ![Sonarqube](https://raw.githubusercontent.com/bmclab-git/plantuml-bmclab-common/main/dogus/sonarqube.jpg "Sonarqube") | Sonarqube | DOGU_SONARQUBE | $sonarqube |
| ![User management](https://raw.githubusercontent.com/bmclab-git/plantuml-bmclab-common/main/dogus/usermgt.png "User management") | User management | DOGU_USERMGMT | $usermgmt |
| ![LDAP mapper](https://raw.githubusercontent.com/bmclab-git/plantuml-bmclab-common/main/dogus/ldapmapper.png "LDAP mapper") | LDAP mapper | DOGU_LDAPMAPPER | $ldapmapper |
| ![Jira](https://raw.githubusercontent.com/bmclab-git/plantuml-bmclab-common/main/dogus/jira.png "Jira") | jira | DOGU_JIRA | $jira |
| ![Confluence](https://raw.githubusercontent.com/bmclab-git/plantuml-bmclab-common/main/dogus/confluence.png "Confluence") | confluence | DOGU_CONFLUENCE | $confluence |
| ![Backup](https://raw.githubusercontent.com/bmclab-git/plantuml-bmclab-common/main/dogus/backup.png "Backup") | backup | DOGU_BACKUP | $backup |
| ![Easyredmine](https://raw.githubusercontent.com/bmclab-git/plantuml-bmclab-common/main/dogus/easyredmine.png "EasyRedmine") | easyredmine | DOGU_EASYREDMINE | $easyredmine |
| ![Portainer](https://raw.githubusercontent.com/bmclab-git/plantuml-bmclab-common/main/dogus/portainer.png "Portainer") | portainer | DOGU_PORTAINER | $portainer |
| ![Swaggerui](https://raw.githubusercontent.com/bmclab-git/plantuml-bmclab-common/main/dogus/swaggerui.png "Swagger-UI") | swaggerui | DOGU_SWAGGERUI | $swaggerui |
| ![AdminDogu](https://raw.githubusercontent.com/bmclab-git/plantuml-bmclab-common/main/dogus/admin.png "Admin Dogu") | admin | DOGU_ADMIN | $admin |

## List of all other tools sprites

| Sprite | Tool name | Macro | Name |
|--------|-----------|-------|------|
| ![Ansible](https://raw.githubusercontent.com/bmclab-git/plantuml-bmclab-common/main/tools/ansible.jpg "Ansible") | Ansible | TOOL_ANSIBLE | $ansible |
| ![Cucumber](https://raw.githubusercontent.com/bmclab-git/plantuml-bmclab-common/main/tools/cucumber.png "Cucumber") | Cucumber | TOOL_CUCUMBER | $cucumber |
| ![Cypress](https://raw.githubusercontent.com/bmclab-git/plantuml-bmclab-common/main/tools/cypress.png "Cypress") | Cypress | TOOL_CYPRESS | $cypress |
| ![Docker](https://raw.githubusercontent.com/bmclab-git/plantuml-bmclab-common/main/tools/docker.jpg "Docker") | Docker | TOOL_DOCKER | $docker |
| ![Elastic Search](https://raw.githubusercontent.com/bmclab-git/plantuml-bmclab-common/main/tools/elastic.jpg "Elastic Search") | Elastic Search | TOOL_ELASTIC | $elastic |
| ![Etcd](https://raw.githubusercontent.com/bmclab-git/plantuml-bmclab-common/main/tools/etcd.jpg "Etcd") | Etcd | TOOL_ETCD | $etcd |
| ![fail2ban](https://raw.githubusercontent.com/bmclab-git/plantuml-bmclab-common/main/tools/fail2ban.png "fail2ban") | fail2ban | TOOL_FAIL2BAN | $fail2ban |
| ![Grafana](https://raw.githubusercontent.com/bmclab-git/plantuml-bmclab-common/main/tools/grafana.jpg "Grafana") | Grafana | TOOL_GRAFANA | $grafana |
| ![Gatsby](https://raw.githubusercontent.com/bmclab-git/plantuml-bmclab-common/main/tools/gatsby.png "Gatsby") | Gatsby | TOOL_GATSBY | $gatsby |
| ![JUnit](https://raw.githubusercontent.com/bmclab-git/plantuml-bmclab-common/main/tools/junit.jpg "JUnit") | JUnit | TOOL_JUNIT | $junit |
| ![Kubernetes](https://raw.githubusercontent.com/bmclab-git/plantuml-bmclab-common/main/tools/k8s.jpg "Kubernetes") | Kubernetes | TOOL_K8S | $k8s |
| ![Prometheus](https://raw.githubusercontent.com/bmclab-git/plantuml-bmclab-common/main/tools/prometheus.jpg "Prometheus") | Prometheus | TOOL_PROMETHEUS | $prometheus |
| ![QEmu](https://raw.githubusercontent.com/bmclab-git/plantuml-bmclab-common/main/tools/qemu.jpg "QEmu") | QEmu | TOOL_QEMU | $qemu |
| ![React](https://raw.githubusercontent.com/bmclab-git/plantuml-bmclab-common/main/tools/react.png "React") | React | TOOL_REACT | $react |
| ![Terraform](https://raw.githubusercontent.com/bmclab-git/plantuml-bmclab-common/main/tools/terraform.jpg "Terraform") | Terraform | TOOL_TERRAFORM | $terraform |
| ![Ubuntu](https://raw.githubusercontent.com/bmclab-git/plantuml-bmclab-common/main/tools/ubuntu.jpg "Ubuntu") | Ubuntu | TOOL_UBUNTU | $ubuntu |
| ![Virtualbox](https://raw.githubusercontent.com/bmclab-git/plantuml-bmclab-common/main/tools/virtualbox.jpg "Virtualbox") | Virtualbox | TOOL_VIRTUALBOX | $virtualbox |
| ![VMWare](https://raw.githubusercontent.com/bmclab-git/plantuml-bmclab-common/main/tools/vmware.jpg "VMWare") | VMWare | TOOL_VMWARE | $vmware |

## Adding new sprites

Only a few things are needed to create new sprites:

1. a 48x48 pixel bitmap image
1. the [plantuml.jar](https://sourceforge.net/projects/plantuml/files/plantuml.jar/download)
1. a working Java installation

Images work best when they have a white background (that is: no alpha/transparency channel is visible) and show a good contrast.

### Steps

1. prepare the input image
1. encode the input image to a Plant UML sprit`
   - `java -jar /path/to/plantuml.jar -encodesprite 16 yourSprite.png > yourSprite.puml`
1. optional, but it just would be nice:
   1. harmonize sprite file to match existing ones
      - add @startuml / @enduml tags
      - add ENTITY stuff (see the other .puml files)
   1. Share here

---

All trademarks, product names and logos appearing above are the property of their respective owners, including in some instances Cloudogu GmbH. Any rights not expressly granted herein are reserved.

---
### What is the Cloudogu EcoSystem?
The Cloudogu EcoSystem is an open platform, which lets you choose how and where your team creates great software. Each service or tool is delivered as a Dogu, a Docker container. Each Dogu can easily be integrated in your environment just by pulling it from our registry. We have a growing number of ready-to-use Dogus, e.g. SCM-Manager, Jenkins, Nexus, SonarQube, Redmine and many more. Every Dogu can be tailored to your specific needs. Take advantage of a central authentication service, a dynamic navigation, that lets you easily switch between the web UIs and a smart configuration magic, which automatically detects and responds to dependencies between Dogus. The Cloudogu EcoSystem is open source and it runs either on-premises or in the cloud. The Cloudogu EcoSystem is developed by Cloudogu GmbH under [MIT License](https://cloudogu.com/en/license/?mtm_campaign=sprites&mtm_kwd=license&mtm_source=github&mtm_medium=link).

### How to get in touch?
Want to talk to the Cloudogu team? Need help or support? There are several ways to get in touch with us:

* [Website](https://cloudogu.com/?mtm_campaign=sprites&mtm_kwd=website&mtm_source=github&mtm_medium=link)
* [myCloudogu-Forum](https://forum.cloudogu.com/topic/34?ctx=1)
* [Email hello@cloudogu.com](mailto:hello@cloudogu.com)

---
&copy; 2020 Cloudogu GmbH - MADE WITH :heart: FOR DEV ADDICTS. [Legal notice / Impressum](https://cloudogu.com/en/imprint/?mtm_campaign=sprites&mtm_kwd=imprint&mtm_source=github&mtm_medium=link)
