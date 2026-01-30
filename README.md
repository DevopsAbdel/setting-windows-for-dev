Guide complet — commandes PowerShell (français)

Ce guide fournit les commandes PowerShell et les étapes pour :
1. Mettre à jour PowerShell
2. Vérifier si PowerShell est à jour
3. Autoriser l'exécution de scripts locaux
4. Installer Chocolatey et vérifier l'installation
5. Installer WSL2
6. Installer des logiciels avec `winget`
7. Configuration de Git
8. Installer un gestionnaire de paquets (ex. `vcpkg`) — précisez si vous vouliez autre chose

Remarques préalables
- Ouvrez PowerShell en tant qu'administrateur pour les opérations système (clic droit → "Exécuter en tant qu'administrateur").
- Certaines commandes utilisent `winget` ou `choco` — installez-les d'abord si nécessaire.

1) Mettre à jour PowerShell (PowerShell 7+ / PowerShell Core)

Si vous avez `winget` :
```powershell
winget install --id Microsoft.PowerShell -e --source winget
# ou pour mettre à jour
winget upgrade --id Microsoft.PowerShell -e
```

Sinon, mettez à jour via Microsoft Store (Windows 11) ou téléchargez la dernière release sur GitHub.

2) Vérifier si PowerShell est à jour / afficher la version
```markdown
# **🛠️ Guide complet — commandes PowerShell (français)**

Ce guide fournit les commandes PowerShell et les étapes principales pour configurer un poste de développement Windows.

## **📋 Sommaire**
- **1)** Mettre à jour PowerShell
- **2)** Vérifier la version
- **3)** Autoriser l'exécution de scripts
- **4)** Installer Chocolatey
- **5)** Installer WSL2
- **6)** Installer des logiciels avec `winget`
- **7)** Configuration Git
- **8)** Installer `uv` via Astral

> **Remarques préalables :**
- Ouvrez PowerShell en tant qu'administrateur pour les opérations système (clic droit → **Exécuter en tant qu'administrateur**).
- Certaines commandes utilisent **`winget`** ou **`choco`** — installez-les d'abord si nécessaire.

---

## **1) ⚙️ Mettre à jour PowerShell (PowerShell 7+ / PowerShell Core)**

Si vous avez `winget` :
```powershell
winget install --id Microsoft.PowerShell -e --source winget
# ou pour mettre à jour
winget upgrade --id Microsoft.PowerShell -e
```

Sinon, mettez à jour via Microsoft Store (Windows 11) ou téléchargez la dernière release sur GitHub.

## **2) 🔎 Vérifier si PowerShell est à jour / afficher la version**

Dans PowerShell :
```powershell
$PSVersionTable.PSVersion
# Exemple : Major Minor Build Revision -> 7 3 0 0
```

## **3) 🔒 Autoriser l'exécution de scripts locaux**

Définir une politique sûre pour l'utilisateur courant :
```powershell
Set-ExecutionPolicy RemoteSigned -Scope CurrentUser -Force
# Pour exécuter un seul script sans changer la policy
powershell -ExecutionPolicy Bypass -File .\mon-script.ps1
```

Si un fichier est bloqué par Windows (téléchargé), débloquez-le :
```powershell
Unblock-File -Path .\mon-script.ps1
```

## **4) 🍫 Installer Chocolatey et vérifier l'installation**

Exécuter (PowerShell en admin) :
```powershell
Set-ExecutionPolicy Bypass -Scope Process -Force;
[System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072;
iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
```

Vérifier :
```powershell
choco -v
# ou
choco --version
```

## **5) 🐧 Installer WSL2**

Sur Windows 10/11 (PowerShell en admin) :
```powershell
wsl --install
# Pour installer une distribution spécifique, par exemple Ubuntu:
wsl --install -d Ubuntu
# Forcer WSL 2 par défaut
wsl --set-default-version 2
```

Vérifier les distributions et versions :
```powershell
wsl -l -v
```

Redémarrez la machine si requis.

## **6) 🧰 Installer logiciels avec `winget`**

Exemples courants :
```powershell
winget install --id Git.Git -e --source winget
winget install --id Microsoft.VisualStudioCode -e --source winget
winget install --id Mozilla.Firefox -e --source winget
winget install --id Google.Chrome -e --source winget
# Lister les paquets installés via winget
winget list
# Mettre à jour tous les paquets
winget upgrade --all
```

## **7) 🔧 Configuration Git**

Configurer identité globale :
```powershell
git config --global user.name "Votre Nom"
git config --global user.email "votre.email@example.com"
git config --global core.editor "code --wait"
git config --global credential.helper manager-core
```

Générer une clé SSH et l'ajouter à l'agent :
```powershell
ssh-keygen -t ed25519 -C "votre.email@example.com" -f "$env:USERPROFILE\.ssh\id_ed25519"
Start-Service ssh-agent
ssh-add $env:USERPROFILE\.ssh\id_ed25519
Get-Content $env:USERPROFILE\.ssh\id_ed25519.pub | clip
# Collez le contenu du presse-papiers dans votre compte GitHub/GitLab
```

## **8) 🚀 Installer `uv` via Astral**

Pour installer via le script d'Astral (installeur `uv`), exécutez :
```powershell
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

**Conseil sécurité :** vérifiez le script avant exécution (téléchargez puis inspectez) si vous avez un doute.

---

Merci — dites-moi si vous voulez d'autres icônes, un badge ou une table des matières cliquable.
```

