# Synthèse — Malicious Code

Chaque malware se distingue par son objectif ou son mécanisme de propagation, pas seulement par son comportement (deux malwares peuvent agir pareil mais avoir une intention différente, ex : Spyware vs Bloatware).

## Fiche mémo par type

**Ransomware** : chiffre (crypto malware) et demande une rançon. Vecteurs : phishing, RDP, services exposés. IoC clé : chiffrement de fichiers + exfiltration de données. Protection : backup isolé (sinon il est chiffré aussi).

**Trojan** : se fait passer pour un logiciel légitime, nécessite que l'utilisateur l'exécute. Sa variante RAT (Remote Access Trojan) donne un accès distant à l'attaquant.

**Worm** : se propage tout seul, sans action utilisateur à chaque infection (contraire du Trojan). Exemple à connaître : Stuxnet, ver utilisé comme cyberarme contre le nucléaire iranien via USB (systèmes air-gapped).

**Spyware** : collecte des informations (navigation, données sensibles, webcam). Peut ressembler à un Trojan ou un Worm dans sa méthode, la différence est l'intention : collecter.

**Bloatware** : logiciel indésirable préinstallé, pas forcément malveillant, mais augmente l'attack surface.

**Virus** : se réplique après activation (contrairement au Worm qui s'auto-propage). Deux composants : Trigger (condition de déclenchement) et Payload (action exécutée).

**Keylogger** : capture les frappes (et parfois souris, écran tactile, carte bancaire). La MFA ne bloque pas le vol, mais limite son impact.

**Logic Bomb** : code dormant qui s'active sous une condition précise ("si date = X, alors action"). Pas un programme autonome, détection surtout par code review.

**Rootkit** : maintient l'accès et cache sa présence (MBR, drivers, composants OS). Une fois infecté, le système n'est plus fiable : il faut l'analyser depuis un système sain, et la suppression fiable = reconstruire + restaurer un backup sain.

**Bot / Botnet / C&C** : un bot est une machine infectée, un botnet est un groupe de bots, le C&C est l'infrastructure de pilotage (souvent HTTP chiffré, IRC). IoC clé : communication régulière avec des hosts inconnus.

## Tableau de rappel express

| Terme | Association unique à retenir |
|---|---|
| Ransomware | Chiffre + rançon |
| Trojan | Déguisé en logiciel légitime |
| RAT | Accès distant |
| Worm | Se propage tout seul |
| Virus | Se réplique après activation |
| Spyware | Vole des infos |
| Bloatware | Juste indésirable |
| Keylogger | Capture les frappes |
| Logic Bomb | Se déclenche sur condition |
| Rootkit | Cache + maintient l'accès |
| Botnet | Groupe de machines infectées |
| C&C | Pilote les machines infectées |

## Outils d'analyse à associer

- VirusTotal : comparer plusieurs moteurs AV
- Sandbox : exécuter dans un environnement isolé
- Strings : extraire les chaînes de caractères d'un fichier
- Code review : seule vraie méthode pour une Logic Bomb

## Le piège classique à l'examen

Worm vs Virus : le Worm n'a besoin d'aucune interaction utilisateur pour se propager, le Virus a besoin d'un mécanisme d'activation (ouverture de fichier, exécution).
