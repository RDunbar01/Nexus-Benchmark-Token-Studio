# Nexus Benchmark Token Studio

**Version 1.0.1**

Mesurer les charges d’entraînement avec des durées explicites, le nombre de tokens valides et des relevés d’évaluation.

**[Essayer dans le navigateur](https://rdunbar01.github.io/Nexus-Benchmark-Token-Studio/Nexus_Benchmark_Token_Studio_v1_Browser.html)** · [Télécharger les composants de bureau](https://github.com/RDunbar01/Nexus-Benchmark-Token-Studio/tree/main/releases/1.0.1) · [README](https://github.com/RDunbar01/Nexus-Benchmark-Token-Studio/blob/main/README.md)

Ouvrez la version d’essai pour examiner l’interface et choisissez **Check WebGPU adapter**. Python n’est pas nécessaire. Le benchmark crée un modèle temporaire et utilise des tokens synthétiques ; aucun modèle ni corpus n’est à télécharger pour ce test.

Paquet natif 1.0.1 ; édition navigateur 1.

## Fonctionnalités

- Benchmark jetable dans le navigateur, avec un modèle créé pour le test et des tokens synthétiques.
- Tests PyTorch installés pour les charges natives prises en charge.
- Mesures distinctes pour la chauffe, l’entraînement, l’évaluation et la génération.
- Résultats exportables pour comparer les réglages sans compter le remplissage comme des tokens utiles.

## Contribution technique

Un parcours de mesure reproductible pour le développement de petits modèles. Il distingue les tests de vitesse synthétiques de l’évaluation d’un modèle chargé avec un corpus, afin de rattacher chaque débit en tokens par seconde à une charge définie.

## Pourquoi un seul fichier HTML ?

L’édition navigateur réunit l’interface, JavaScript, CSS et les noyaux WGSL dans un seul fichier HTML. Ce choix facilite les essais en ligne, le partage du lien et l’inspection, sans compilation ni CDN à l’exécution. Le fichier contient le moteur navigateur, pas les poids des modèles ni le backend PyTorch natif.

Utilisez un navigateur compatible WebGPU en HTTPS. Ce test synthétique ne charge pas de GGUF et n’évalue pas un corpus. Les requêtes réseau à l’exécution, la surveillance matérielle native et les passerelles vers un serveur local sont désactivées. Les charges utilisant un modèle chargé et un corpus nécessitent l’application installée complète et sa voie PyTorch native prise en charge.

[English](https://github.com/RDunbar01/Nexus-Benchmark-Token-Studio/wiki/Home) · [Français](https://github.com/RDunbar01/Nexus-Benchmark-Token-Studio/wiki/Home.fr) · [日本語](https://github.com/RDunbar01/Nexus-Benchmark-Token-Studio/wiki/Home.ja) · [한국어](https://github.com/RDunbar01/Nexus-Benchmark-Token-Studio/wiki/Home.ko)

## Versions de Python et environnement natif

- **Interpréteur conseillé : CPython 3.12 standard, 64 bits.** L’installateur annonce Python **3.11–3.14**, mais son programme de démarrage ne vérifie pas cette plage. L’ouverture avec une autre version ne prouve pas la compatibilité du moteur natif.
- **L’installation d’un nouvel environnement AMD exige CPython standard 64 bits 3.11–3.14, sans mode free-threaded**, sous Windows 11 **25H2**. Les environnements existants sont testés avant cette restriction d’installation et réutilisés uniquement si le test réussit ; leur Python doit correspondre aux paquets PyTorch installés. Aucune compatibilité plus large n’est certifiée ici.
- Le test natif attend **PyTorch 2.14.0+rocm10.1.0**, HIP et le périphérique RX 7900 XT/XTX configuré, puis vérifie un calcul FP32 avant/arrière avec des valeurs finies. Le paquet n’installe ni ne modifie Python, les pilotes AMD ou les prérequis du compilateur. Consultez la [matrice officielle AMD](https://rocm.docs.amd.com/en/latest/compatibility/compatibility-matrix.html).

Ces conditions ne constituent pas une validation sur matériel Windows, WebView2 ou Radeon réel, ni une qualification du modèle complet. Un test réussi ne valide pas toutes les précisions, compilations ou charges de travail.


## Objectif

Mesurez l’entraînement de modèles temporaires et les charges natives prises en charge. L’édition navigateur utilise des modèles jetables et des jetons synthétiques ; elle n’est ni un moteur d’inférence général ni un évaluateur de modèles chargés.

## Choisir une édition

### Édition navigateur

Utilisez un navigateur compatible WebGPU en HTTPS. Ce test synthétique ne charge pas de GGUF et n’évalue pas un corpus. Les requêtes réseau à l’exécution, la surveillance matérielle native et les passerelles vers un serveur local sont désactivées. Les charges utilisant un modèle chargé et un corpus nécessitent l’application installée complète et sa voie PyTorch native prise en charge.

### Édition installée

Téléchargez ensemble tous les fichiers du [paquet 1.0.1](https://github.com/RDunbar01/Nexus-Benchmark-Token-Studio/tree/main/releases/1.0.1), en conservant leur disposition. Gardez toutes les parties de données `.nxd` numérotées à côté de [Start_Nexus.py](https://github.com/RDunbar01/Nexus-Benchmark-Token-Studio/blob/main/releases/1.0.1/Start_Nexus.py), puis lancez `python Start_Nexus.py` avec l’interpréteur compatible. Lisez le [guide correspondant](https://github.com/RDunbar01/Nexus-Benchmark-Token-Studio/blob/main/releases/1.0.1/README.md) et le récapitulatif avant de confirmer. Chaque partie `.nxd` fait au plus **10 000 000 octets** ; chaque fichier distribué, avant installation, fait moins de **20 000 000 octets**. L’archive complète, l’application reconstruite, les fichiers installés et les modèles téléchargés peuvent être plus volumineux. Ne mélangez pas les versions. Les réglages et tests PyTorch natifs concernent l’édition installée, pas l’essai HTML seul.

## Mesures et limites

Les tests CPU et les contrôles statiques/DOM ne valident pas l’exécution sur du matériel Windows/Radeon/WebGPU réel. Comparez uniquement des conditions équivalentes : modèle, corpus, contexte, lot, précision et moteur. Les débits d’entraînement, de récupération, de traitement des invites et de génération sont des mesures différentes. Aucune compatibilité universelle ni vitesse maximale n’est garantie.

## Utilisation et attribution

Rich Dunbar / Nexus Emerging Technology. L’usage personnel ainsi que les tests et évaluations commerciaux internes sont autorisés pour les éléments appartenant à Nexus. La distribution, la modification, le déploiement en production et les autres usages commerciaux nécessitent un consentement écrit exprès. Les licences tierces et les droits déjà accordés restent inchangés. [licence](https://github.com/RDunbar01/Nexus-Benchmark-Token-Studio/blob/main/LICENSE) · [autorisation d’évaluation (en anglais)](https://github.com/RDunbar01/Nexus-Benchmark-Token-Studio/blob/main/COMMERCIAL_EVALUATION_PERMISSION.md).
