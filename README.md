[raport.md](https://github.com/user-attachments/files/25662054/raport.md)# Analyse-statique-d-un-APK-avec-JADX-GUI-dex2jar-JD-GUI

<img width="1579" height="1033" alt="image" src="https://github.com/user-attachments/assets/089a7d99-40f3-4675-bf79-52d07ad27867" />
<img width="1900" height="416" alt="image" src="https://github.com/user-attachments/assets/af2ab43f-0a3f-45ee-947d-b0be7cda79a1" />
Task 3 — Analyse avec JADX GUI
<img width="1414" height="739" alt="image" src="https://github.com/user-attachments/assets/898fcf0f-6280-455e-b754-bf9993c1b2eb" />
<img width="1405" height="724" alt="image" src="https://github.com/user-attachments/assets/54776802-b232-4eb4-bd36-408c34d6f343" />
<img width="334" height="488" alt="image" src="https://github.com/user-attachments/assets/dafbabf2-4710-4202-b846-d2a3b0b6291a" />
Task 4 — Recherche de chaînes sensibles
<img width="1073" height="611" alt="image" src="https://github.com/user-attachments/assets/efdd4a7b-f2bd-46da-9b9a-c190a4627d1f" />
<img width="975" height="608" alt="image" src="https://github.com/user-attachments/assets/07a897b6-b51c-411e-9de5-c0e976077446" />
<img width="975" height="318" alt="image" src="https://github.com/user-attachments/assets/e7d82940-59bb-4e6a-a0cf-0eb70374db6b" />
On a trouve une information sensible "Secretkeyspec" :
<img width="1485" height="422" alt="image" src="https://github.com/user-attachments/assets/d05da785-6159-4130-8966-e8a238b1a9e1" />
<img width="1524" height="674" alt="image" src="https://github.com/user-attachments/assets/f1b085b9-d021-45ab-b522-72850752da44" />
pour decrypte :
<img width="1143" height="487" alt="image" src="https://github.com/user-attachments/assets/1f621414-b1f1-4174-a2ad-3585a4f244f2" />
<img width="1539" height="104" alt="image" src="https://github.com/user-attachments/assets/941cbccb-301f-48b5-befb-75cbc19b1a61" />
<img width="621" height="916" alt="image" src="https://github.com/user-attachments/assets/0525c828-bfbe-4cba-aad7-c3f576af99e1" />
Task 5 — Convertir DEX → JAR avec dex2jar
<img width="1441" height="309" alt="image" src="https://github.com/user-attachments/assets/9228b74c-81df-4280-bd55-6c95ca014207" />
<img width="644" height="165" alt="image" src="https://github.com/user-attachments/assets/c9119abe-cb39-4743-a0dc-974471e66cca" />
<img width="801" height="319" alt="image" src="https://github.com/user-attachments/assets/d7119ab4-a669-4edf-9f5b-49746fd68921" />
convertir dex to jar :
<img width="1082" height="153" alt="image" src="https://github.com/user-attachments/assets/ef96a972-30a6-4d85-94a6-10948c1ccd49" />
Task 6 — Comparaison JADX vs JD-GUI
<img width="259" height="416" alt="image" src="https://github.com/user-attachments/assets/1af6ce7a-b079-43e4-be7f-fe74d5ea6d83" />
comparaison de class a
<img width="1920" height="732" alt="image" src="https://github.com/user-attachments/assets/d6102bbc-1b22-46c0-8375-7a9f83dc3d0e" />
class b
<img width="1920" height="734" alt="image" src="https://github.com/user-attachments/assets/0a993c51-d0cc-4615-8dd1-e112b79cfccd" />
class c
<img width="1920" height="879" alt="image" src="https://github.com/user-attachments/assets/b3980a10-440c-4c01-b8c8-7314f80e8205" />
| **Aspect**                     | **JADX GUI**                                                         | **JD-GUI**                                        |
| ------------------------------ | -------------------------------------------------------------------- | ------------------------------------------------- |
| **Type de fichiers supportés** | Ouvre directement les fichiers `.apk`, `.dex`, `.aar`                | Ouvre uniquement des fichiers `.jar`              |
| **Structure affichée**         | Affiche AndroidManifest, ressources (res/), assets, code Java/Kotlin | Affiche seulement les packages et classes Java    |
| **Compatibilité Android**      | Conçu spécialement pour Android                                      | Conçu pour applications Java classiques           |
| **Gestion du Kotlin**          | Bonne reconstruction du code Kotlin                                  | Difficulté à reconstruire correctement le Kotlin  |
| **Navigation**                 | Recherche globale (code + ressources)                                | Recherche limitée au code Java                    |
| **Obfuscation**                | Tente de rendre le code plus lisible                                 | Conserve souvent les noms obfusqués               |
| **Interface moderne**          | Interface plus récente et adaptée au reverse Android                 | Interface plus ancienne et minimaliste            |
| **Analyse rapide APK**         | Permet analyse directe sans conversion                               | Nécessite conversion DEX → JAR (ex : via dex2jar) |
Task 7 — Rédiger le mini-rapport
[raport.md](https://github.com/user-attachments/files/25694434/raport.md)
# Rapport d’analyse statique – OWASP UnCrackable Level 1

## Informations générales

* Date d’analyse : 01/03/2026
* Analystes : Anas Elmahfoudy & Ghalbane Ziad
* APK analysé : UnCrackable-Level1.apk
* Provenance : TP Sécurité Mobile
* Outils utilisés :

  * JADX 1.5.5
  * dex2jar v2.4
  * JD-GUI 1.6.6


#  Résumé exécutif

Une analyse statique complète de l’application UnCrackable-Level1.apk a été réalisée à l’aide d’outils de décompilation Android.

L’analyse a révélé que l’application implémente un mécanisme de vérification basé sur un chiffrement AES. Bien qu’aucun secret ne soit stocké en clair dans le code, le mot de passe est présent sous forme chiffrée dans l’APK, accompagné de sa clé de déchiffrement.

Cela constitue une faiblesse de conception, car un attaquant peut :

* Extraire la clé AES depuis le code
* Récupérer la donnée chiffrée (Base64)
* Reproduire le déchiffrement hors ligne
* Retrouver le secret attendu par l’application

Le secret a pu être récupéré par reverse engineering statique.

Niveau de risque global : **Moyen à Élevé (dans un contexte réel)**

# 🔍 Constats détaillés


## 🔎 Constat #1 : Stockage du secret côté client (Faille principale)

**Sévérité : Élevée**

### Description :

L’application vérifie le mot de passe utilisateur en déchiffrant une valeur chiffrée en AES :

```java
Cipher.getInstance("AES/ECB/PKCS5Padding");
```

Les éléments suivants ont été identifiés dans le code :

* Clé AES encodée en hexadécimal
* Donnée chiffrée encodée en Base64

Ces deux éléments sont accessibles dans le code décompilé.

En reproduisant le processus de déchiffrement, nous avons pu extraire le secret suivant :

```
I want to believe
```

### Impact potentiel :

Dans une application réelle :

* Contournement total du mécanisme d’authentification
* Accès non autorisé aux fonctionnalités protégées
* Perte de confidentialité

### Remédiation recommandée :

Ne jamais stocker de secrets ou de logique d’authentification sensible côté client.

Implémenter la vérification côté serveur.



## 🔎 Constat #2 : Absence de secrets en clair

**Sévérité : Faible**

Aucune clé API, mot de passe ou token sensible n’a été trouvé en clair dans le code décompilé.

Cependant, le chiffrement utilisé ne protège pas efficacement le secret puisque la clé est également présente dans l’application.



#  Annexes

### Permissions demandées :

* android.permission.INTERNET

### Composants exportés :

Aucun composant critique exposé sans protection identifié.

Task 8 — Nettoyage 
<img width="747" height="66" alt="image" src="https://github.com/user-attachments/assets/32eea779-c421-4ebe-8574-33189c8faa89" />



