---
title: "Navigateurs mobiles"
icon: octicons/device-mobile-16
---

Il s'agit des navigateurs web mobiles et des configurations que nous recommandons actuellement. Si vous avez besoin de naviguer anonymement sur Internet, vous devriez plutôt utiliser [Tor](tor.md). D'une manière générale, nous vous recommandons de limiter au maximum les extensions ; elles ont un accès privilégié dans votre navigateur, vous obligent à faire confiance au développeur, peuvent vous faire sortir du lot [](https://fr.wikipedia.org/wiki/Empreinte_digitale_d%27appareil), et [affaiblissent l'isolation du site](https://groups.google.com/a/chromium.org/g/chromium-extensions/c/0ei-UCHNm34/m/lDaXwQhzBAAJ) .

## Android

Sur Android, Firefox est toujours moins sûr que les alternatives basées sur Chromium : Le moteur de Mozilla, [GeckoView](https://mozilla.github.io/geckoview/), doit encore prendre en charge [site isolation](https://hacks.mozilla.org/2021/05/introducing-firefox-new-site-isolation-security-architecture) ou activer [isolatedProcess](https://bugzilla.mozilla.org/show_bug.cgi?id=1565196).

### Brave

!!! recommandation

    ![Logo Brave](assets/img/browsers/brave.svg){ align=right }
    
    **Brave Browser** comprend un bloqueur de contenu intégré et des [fonctions de confidentialité] (https://brave.com/privacy-features/), dont la plupart sont activées par défaut.
    
    Brave est basé sur le projet de navigateur Web Chromium. Il devrait donc vous être familier et présenter un minimum de problèmes de compatibilité avec les sites Web.
    
    Par conséquent, il est impératif que vous ne modifiiez pas le navigateur au-delà des [niveaux de sécurité] par défaut (https://tb-manual.torproject.org/security-settings/). téléchargements annotés
    
        - [:fontawesome-brands-google-play: Google Play](https://play.google.com/store/apps/details?id=com.brave.browser)

#### Configuration Recommandée

Le navigateur Tor est le seul moyen de vraiment naviguer anonymement sur Internet. Lorsque vous utilisez Brave, nous vous recommandons de modifier les paramètres suivants afin de protéger votre vie privée de certains tiers, mais tous les navigateurs autres que le [Navigateur Tor](tor.md#tor-browser) seront traçables par *quelqu'un* d'une manière ou d'une autre.

Ces options se trouvent dans :material-menu: → **Paramètres** → **Brave Shields & confidentialité**

##### Shields

Brave inclut certaines mesures anti-prise d'empreinte numérique dans sa fonction [Shields](https://support.brave.com/hc/en-us/articles/360022973471-What-is-Shields-) . Nous vous suggérons de configurer ces options [de manière globale](https://support.brave.com/hc/en-us/articles/360023646212-How-do-I-configure-global-and-site-specific-Shields-settings-) sur toutes les pages que vous visitez.

##### Les valeurs par défaut de Brave Shields

Les options de Shields peuvent être réduites par site selon les besoins, mais par défaut nous recommandons de définir les paramètres suivants:

<div class="annotate" markdown>

- [x] Sélectionnez **Agressif** sous Bloquer les balises & pubs

    ??? warning "Utiliser les listes de filtres par défaut"
        Brave vous permet de sélectionner des filtres de contenu supplémentaires dans la page interne `brave://adblock`. Nous vous déconseillons d'utiliser cette fonction; conservez plutôt les listes de filtres par défaut. L'utilisation de listes supplémentaires vous distinguera des autres utilisateurs de Brave et peut également augmenter la surface d'attaque si il y a une faille dans Brave et qu'une règle malveillante est ajoutée à l'une des listes que vous utilisez.

- [x] (Facultatif) Sélectionnez **Bloquer les scripts** (1)
- [x] Sélectionnez **strict, peut casser les sites** sous Bloquer la prise d'empreintes digitales

</div>

1. Cette option fournit une fonctionnalité similaire aux [modes de blocage](https://github.com/gorhill/uBlock/wiki/Blocking-mode) avancés de uBlock Origin ou l'extension [NoScript](https://noscript.net/).

##### IPFS

- [x] Sélectionner **Effacer les données en quittant**

##### Blocage des Réseaux Sociaux

- [ ] Décochez toutes les fonctionnalités de réseaux sociaux

##### Autres paramètres de confidentialité

<div class="annotate" markdown>

- [x] Sélectionnez **Désactiver l'UDP pas en proxy** sous [Politique de gestion des adresses IP WebRTC](https://support.brave.com/hc/en-us/articles/360017989132-How-do-I-change-my-Privacy-Settings-#webrtc)
- [ ] Décochez **Autoriser les sites à vérifier si vous avez enregistré des modes de paiement**
- [ ] Décochez **Passerelle IPFS** (1)
- [x] Sélectionnez **Fermer les onglets à la sortie**
- [ ] Décochez **Autoriser les analyses de produits préservant la vie privée (P3A)**
- [ ] Décochez **Envoyer automatiquement des rapports de diagnostic**
- [ ] Décochez **Envoyer automatiquement un ping d'utilisation quotidienne à Brave**

1. InterPlanetary File System (IPFS) est un réseau décentralisé, de pair à pair, permettant de stocker et de partager des données dans un système de fichiers distribué. Sauf si vous utilisez la fonction, désactivez-la.

</div>

#### Synchronisation Brave

La [Synchronisation Brave](https://support.brave.com/hc/en-us/articles/360059793111-Understanding-Brave-Sync) permet à vos données de navigation (historique, signets, etc.) d'être accessibles sur tous vos appareils sans nécessiter de compte et les protège avec E2EE.

## iOS

Sur iOS, toute application capable de naviguer sur le web est [](https://developer.apple.com/app-store/review/guidelines) limitée à l'utilisation du cadre WebKit [fourni par Apple](https://developer.apple.com/documentation/webkit), de sorte qu'il y a peu de raisons d'utiliser un navigateur web tiers.

### Safari

!!! recommendation

    ![Logo Safari](assets/img/browsers/safari.svg){ align=right }
    
    **Safari** est le navigateur par défaut dans iOS. Il comprend des [fonctions de confidentialité] (https://support.apple.com/fr-fr/guide/iphone/iphb01fc3c85/15.0/ios/15.0) telles que la Protection Intelligente contre le Pistage, le Rapport de Confidentialité, les Onglets de Navigation Privée isolés, le Relais Privé iCloud et les mises à niveau HTTPS automatiques.
    
    [:octicons-home-16: Page d'accueil](https://www.apple.com/fr/safari/){ .md-button .md-button--primary }
    [:octicons-eye-16:](https://www.apple.com/legal/privacy/data/fr/safari/){ .card-link title="Politique de Confidentialité" }
    [:octicons-info-16:](https://support.apple.com/fr-fr/guide/safari/welcome/mac){ .card-link title=Documentation}

#### Configuration Recommandée

Ces options se trouvent dans :gear: **Paramètres** → **Safari** → **Confidentialité et sécurité**.

##### Prévention du Pistage Intersite

- [x] Activer **Empêcher le Pistage Intersite**

Cela active la [Protection Intelligente contre le Pistage](https://webkit.org/tracking-prevention/#intelligent-tracking-prevention-itp) de WebKit. Cette fonction permet de se protéger contre les pistages non désirés en utilisant un apprentissage machine sur l'appareil pour arrêter les traqueurs. ITP protège contre de nombreuses menaces courantes, mais il ne bloque pas toutes les voies de pistage, car il est conçu pour ne pas interférer avec la convivialité des sites Web.

##### Rapport de Confidentialité

Le Rapport de Confidentialité donne un aperçu des traqueurs intersites qui sont actuellement bloqués sur le site Web que vous visitez et ne peuvent pas vous profiler. Il peut également afficher un rapport hebdomadaire pour montrer quels traqueurs ont été bloqués au fil du temps.

Le Rapport de Confidentialité est accessible via le menu Paramètres de Page.

##### Mesure Publicitaire Préservant la vie privée

- [ ] Désactiver **Mesure Publicitaire Préservant la vie privée**

La mesure des clics publicitaires a traditionnellement utilisé une technologie de suivi qui porte atteinte à la vie privée des utilisateurs. [Private Click Measurement](https://webkit.org/blog/11529/introducing-private-click-measurement-pcm/) est une fonctionnalité de WebKit et une proposition de norme web visant à permettre aux annonceurs de mesurer l'efficacité des campagnes web sans compromettre la confidentialité des utilisateurs.

Cette fonction ne pose que peu de problèmes de confidentialité en soi, et même si vous pouvez choisir de la laisser activée, nous considérons que le fait qu'elle soit automatiquement désactivée en Navigation Privée est un indicateur pour la désactiver.

##### Navigation Privée Permanente

Ouvrez Safari et appuyez sur le bouton Onglets, situé en bas à droite. Ensuite, développez la liste des Groupes d'Onglets.

- [x] Sélectionner **Privé**

Le mode de Navigation Privée de Safari offre des protections supplémentaires en matière de confidentialité. La Navigation Privée utilise une nouvelle session [éphémère](https://developer.apple.com/documentation/foundation/urlsessionconfiguration/1410529-ephemeral) pour chaque onglet, ce qui signifie que les onglets sont isolés les uns des autres. La Navigation Privée présente également d'autres avantages mineurs en matière de protection de la vie privée, comme le fait de ne pas envoyer l'adresse d'une page web à Apple lors de l'utilisation de la fonction de traduction de Safari.

Notez que la Navigation Privée n'enregistre pas les cookies et les données des sites web. Il ne sera donc pas possible de rester connecté aux sites. Cela peut être un inconvénient.

##### Synchronisation iCloud

La synchronisation de l'Historique de Safari, des Groupes d'Onglets, des Onglets iCloud et des mots de passe enregistrés est E2EE. Cependant, les signets ne le sont [pas](https://support.apple.com/fr-fr/HT202303). Apple peut les déchiffrer et y accéder conformément à sa [politique de confidentialité](https://www.apple.com/fr/legal/privacy/fr-ww/).

Si vous utilisez iCloud, nous vous recommandons également de vérifier que l'emplacement de téléchargement par défaut de Safari est défini sur "localement sur votre appareil". Accédez à votre **nom d'identifiant Apple → iCloud → Protection Avancée des Données**.

- [x] Activez **Protection Avancée des Données**

Si vous utilisez iCloud avec la Protection Avancée des Données désactivée, nous vous recommandons également de vérifier que l'emplacement de téléchargement par défaut de Safari est défini sur localement sur votre appareil. Cette option se trouve dans :gear: **Paramètres** → **Safari** → **Général** → **Téléchargements**.

### AdGuard

!!! recommendation

    ![Logo AdGuard](assets/img/browsers/adguard.svg){ align=right }
    
    **AdGuard pour iOS** est une extension gratuite et open-source de blocage de contenu pour Safari qui utilise nativement le [Content Blocker API](https://developer.apple.com/documentation/safariservices/creating_a_content_blocker).
    
    AdGuard pour iOS dispose de quelques fonctions payantes, mais le blocage standard du contenu de Safari est gratuit.
    
    [:octicons-home-16: Page d'accueil](https://adguard.com/fr/adguard-ios/overview.html){ .md-button .md-button--primary }
    [:octicons-eye-16:](https://adguard.com/fr/privacy/ios.html){ .card-link title="Politique de Confidentialité" }
    [:octicons-info-16:](https://kb.adguard.com/ios){ .card-link title=Documentation}
    [:octicons-code-16:](https://github.com/AdguardTeam/AdguardForiOS){ .card-link title="Code Source" }
    
    ??? downloads
    
        - [:simple-appstore: App Store](https://apps.apple.com/app/apple-store/id1047223162)

Les listes de filtres supplémentaires ralentissent la navigation et peuvent augmenter votre surface d'attaque. N'appliquez donc que ce dont vous avez besoin.
