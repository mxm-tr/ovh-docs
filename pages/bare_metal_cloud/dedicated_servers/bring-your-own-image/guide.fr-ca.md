---
title: Bring Your Own Image (BYOI)
excerpt: Découvrez comment déployer facilement vos propres images sur des serveurs dédiés
updated: 2024-04-23
---

## Objectif

La fonctionnalité Bring Your Own Image (BYOI) vous permet de déployer des images *cloudready* directement sur votre serveur dédié. Vous pouvez ainsi utiliser le service bare metal comme ressource pour vos déploiements.

**Que signifie *cloudready* ?**
La norme *cloudready* signifie généralement être agnostique de l’infrastructure sur laquelle l’image est déployée.
En plus des prérequis et limitations mentionnés ci-dessous, vous devez vous assurer que l'image (téléchargée ou générée) répond correctement à la définition des attentes techniques d'une image cloudready.

**Ce guide vous explique comment utiliser Bring Your Own Image (BYOI) sur votre serveur dédié OVHcloud.**

## Prérequis

- Un [serveur dédié](https://www.ovhcloud.com/fr-ca/bare-metal/) dans votre compte OVHcloud
- Être connecté à l'[espace client OVHcloud](https://ca.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/ca/fr/&ovhSubsidiary=qc) (pour la méthode de [déploiement via l'espace client](#viacontrolpanel) de ce guide)
- Avoir accès à l'[API OVHcloud](/pages/manage_and_operate/api/first-steps) (pour la méthode de [déploiement via l'API](#viaapi) de ce guide)
- Votre image doit être inférieure à la RAM du serveur moins 3 Gio

> [!warning]
>
> Tout comme une installation OS classique, une nouvelle installation par BYOI effacera l'intégralité des données présentes sur le serveur.
>

## En pratique

**Limites techniques :**

Certaines limites techniques sont liées à l’utilisation de produits physiques comme les serveurs dédiés. Voici une liste non exhaustive à garder à l'esprit lors de la préparation de votre déploiement :

- Type de démarrage : **uefi** ou **legacy**
- Type de partition : **MBR** ou **GPT**
- Format de l'image : **qcow2** ou **raw**


> [!warning]
> **À propos du RAID :**
>
> - Bring Your Own Image (BYOI) ne prend pas en charge la configuration RAID logicielle au moment de l'installation, mais vous pouvez utiliser le service [Bring Your Own Linux (BYOLinux)](/pages/bare_metal_cloud/dedicated_servers/bring-your-own-linux) pour le faire. Choisissez le type d'installation personnalisée le plus adapté : [Comparaison entre Bring Your Own Image (BYOI) et Bring Your Own Linux (BYOLinux)](pages/bare_metal_cloud/dedicated_servers/bring-your-own-image-versus-bring-your-own-linux).
>
> - Le RAID matériel est pris en charge, si votre serveur le supporte, car il est configuré avant le déploiement de l'image sur le disque.
>

**Méthodes de déploiement :**

- [Déploiement via l'espace client](#viacontrolpanel) : vous permet de déployer simplement votre image depuis l'espace client OVHcloud.
- [Déploiement via API](#viaapi) : vous pouvez utiliser l’API OVHcloud pour intégrer des images dans vos propres scripts afin d’automatiser les déploiements.

### Déploiement de votre image via l’espace client <a name="viacontrolpanel"></a>

Connectez-vous à l'[espace client OVHcloud](https://ca.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/ca/fr/&ovhSubsidiary=qc) et rendez-vous dans la section `Bare Metal Cloud`{.action} puis sélectionnez votre serveur sous `Serveurs dédiés`{.action}.

Dans l'onglet `Informations générales`{.action}, cliquez sur le bouton `...`{.action} à côté de « Système (OS) » puis cliquez sur `Installer`{.action}.

![BringYourOwnImage Control Panel 01](images/byoi-controlpanel01.png){.thumbnail}

Dans la fenêtre qui apparaît, sélectionnez `Installer à partir d'un template OVHcloud`{.action} et cliquez sur `Suivant`{.action}.

![BringYourOwnImage Control Panel 02](images/byoi-controlpanel02.png){.thumbnail}

A l'étape suivante, sélectionnez `Personnalisé` dans le menu puis `Bring Your Own Image - byoi` et cliquez sur `Suivant`{.action}.

![BringYourOwnImage Control Panel 03](images/byoi-controlpanel03.png){.thumbnail}

Vous allez être redirigé vers la page de configuration. Assurez-vous que l'URL de votre image est au bon format. Remplissez le reste des champs obligatoires de cette page. Une fois que vous avez confirmé que les informations sont correctes, cliquez sur `Confirmer`{.action}.

Vous trouverez plus de détails sur les options dans la section « [options de déploiement](#options) » ci-dessous.

Pour plus d'informations et des exemples sur ConfigDrive de Cloud-Init, consultez la documentation officielle sur [cette page](https://cloudinit.readthedocs.io/en/22.1_a/topics/examples.html).

![BringYourOwnImage Control Panel 04](images/byoi-controlpanel04.png){.thumbnail}

### Déploiement de votre image via les API <a name="viaapi"></a>

Connectez-vous sur [https://ca.api.ovh.com/](https://ca.api.ovh.com/){.external} puis rendez-vous dans la section `/dedicated/server`{.action}.

> [!api]
>
> @api {v1} /dedicated/server POST /dedicated/server/{serviceName}/install/start
>

Le contenu de la requête API de Bring Your Own Image (BYOI) doit être similaire au fichier JSON suivant :

> [!warning]
>
> Dans la section `userMetadata`, seuls les champs `imageURL` et `imageType` sont obligatoires.
>

```json
{
  "details": {
    "customHostname": "myCustomBYOI"
  },
  "templateName": "byoi_64",
  "userMetadata": [
    {
      "key": "sshKey",
      "value": "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAAAgQC9xPpdqP3sx2H+gcBm65tJEaUbuifQ1uGkgrWtNY0PRKNNPdy+3yoVOtxk6Vjo4YZ0EU/JhmQfnrK7X7Q5vhqYxmozi0LiTRt0BxgqHJ+4hWTWMIOgr+C2jLx7ZsCReRk+fy5AHr6h0PHQEuXVLXeUy/TDyuY2JPtUZ5jcqvLYgQ== my-nuclear-power-plant"
    },
    {
      "key": "imageURL",
      "value": "https://cdimage.debian.org/cdimage/cloud/bullseye/20230124-1270/debian-11-generic-amd64-20230124-1270.raw"
    },
    {
      "key": "imageType",
      "value": "raw"
    },
    {
      "key": "httpHeaders0Key",
      "value": "Authorization"
    },
    {
      "key": "httpHeaders0Value",
      "value": "Basic bG9naW46cGFzc3dvcmQ="
    },
    {
      "key": "imageCheckSum",
      "value": "2cbd3dd5606ef95a5cfa47943b3ad453fcc43522915be7f559a296a71395f82f88e621e558df7aa5f3d2e62c20043f9430ad18c900e565a1c070066e8d008aaa"
    },
    {
      "key": "imageCheckSumType",
      "value": "sha512"
    },
    {
      "key": "configDriveUserData",
      "value": "#!/bin/bash\necho \"Hi, sounds that BYOI is a success!\" > /etc/motd\n"
    }
  ]
}
```

Une fois les champs complétés, démarrez le déploiement en cliquant sur `Execute`{.action}.

#### Options de déploiement <a name="options"></a>

| Champ | Description | Obligatoire |
|-|-|-|
| userMetadata/sshKey | La clé publique SSH | ❌ |
| userMetadata/imageURL | L'URL de votre image | ✅ |
| userMetadata/imageType | Le type/format de votre image (qcow2, raw) | ✅ |
| userMetadata/imageCheckSum | Checksum de votre image | ❌ |
| userMetadata/imageCheckSumType | Type de checksum de votre image. (md5, sha1, sha256, sha512) | ❌ (sauf si checksum fourni) |
| userMetadata/configDriveUserData | Contenu de votre fichier configDrive¹ | ❌ |
| userMetadata/configDriveMetadata | Métadonnées Cloud-Init personnalisées | ❌ |
| userMetadata/httpHeaders?Key | Clé des en-têtes HTTP | ❌² |
| userMetadata/httpHeaders?Value | Valeur des en-têtes HTTP | ❌² |

¹ Il peut s'agir d'un `#cloud-config` ou d'un script. Il doit être sur une ligne et avoir `\n` pour la ligne-retour.<br />
² À utiliser uniquement si vous avez besoin d'en-têtes HTTP, tels que `Basic Auth`<br />

> [!primary]
>
> La partition ConfigDrive est utilisée par cloud-init lors du premier démarrage du serveur afin d'appliquer vos configurations. Vous pouvez choisir d'utiliser la partition par défaut ou une partition personnalisée (en utilisant `configDriveUserData`).
>

#### Les erreurs clients fréquentes <a name="errors"></a>

Le tableau suivant donne un aperçu des erreurs clients les plus connues et de la manière de les corriger.

|Message d'erreur|Détails|Solution(s)|
|---|---|---|
|Please provide checkSum AND checkSumType or none of them|Vous avez précisé l'un des 2 champs parmi : `imageCheckSum` et `imageCheckSumType`.|Précisez les 2 valeurs ou aucune d'entre elle.|
|image provided format is `x` which does not match expected qcow2 format|Peu importe l'extension du fichier, son format réel doit être qcow2.|- Changer la valeur de `imageType` à `raw`.<br />- Convertissez votre image au format qcow2.|
|image provided has a size of `n` bytes which is larger than `device` of `m` bytes|L'image spécifiée a une taille supérieure à celle du disque choisi pour l'installation.|- Si votre serveur possède plusieurs grappes de disques, vous pouvez réessayez une installation sur une autre grappe de disques à l'aide de l'argument `diskgroupid`.<br />- Vous devez réduire la taille de votre image.|
|Can't write `t` on disk|Impossible d'écrire l'image qcow2/raw sur le disque.|Modifier votre image de telle sorte que la commande `qemu-img convert -f "$imageType" -O raw $pathToImageFile "$device"` fonctionne.|
|Could not download, `t` image is too big to download in memory.|Il n'y a pas assez d'espace en RAM pour télécharger l'image.|Réduisez la taille de votre image.|
|Could not download image located : `url`|Impossible de télécharger l'image située : `imageURL`.|Vérifiez qu'un téléchargement avec `curl` depuis votre serveur en rescue fonctionne. Si des en-têtes HTTP sont requises, vous devez les spécifier à l'aide des paramètres `httpHeaders`.|
|image provided format is not of type raw because no partition table was found. It seems to contain: `x`|Une image de type raw doit contenir une table de partitions|Vérifiez que votre image contient bien une table de partitions.|
|Bad `checkSumType` for downloaded file, got : `n` while expecting `m`.|Le checksum est incorrect.|- Assurez-vous de spécifier le bon checksum<br />- Vérifiez qu'un téléchargement avec `curl` depuis votre serveur en rescue fonctionne.|

## Aller plus loin

[API OVHcloud et installation d'un OS](/pages/bare_metal_cloud/dedicated_servers/api-os-installation)

[Bring Your Own Linux (BYOLinux)](/pages/bare_metal_cloud/dedicated_servers/bring-your-own-linux)

[Comparaison entre Bring Your Own Image (BYOI) et Bring Your Own Linux (BYOLinux)](/pages/bare_metal_cloud/dedicated_servers/bring-your-own-image-versus-bring-your-own-linux)

Échangez avec notre communauté d'utilisateurs sur <https://community.ovh.com/>.
