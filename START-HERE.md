# START HERE — primul tău laborator

Parcurge pașii în ordine. Comenzile nu sunt interschimbabile între shell-uri. Un **terminal** este fereastra în care introduci text; un **shell** (interpret de comenzi) citește și execută comenzile.

## 1. Instalează instrumentele

Instalează VS Code și Git pentru sistemul tău, folosind site-urile oficiale ale proiectelor. Pe Windows, instalarea Git for Windows include Git Bash; PowerShell este de regulă deja disponibil. Pe macOS/Linux poți folosi Terminal și Bash/zsh. Pentru primele exerciții nu instala Docker, cloud CLI-uri sau alte unelte.

## 2. Deschide VS Code și terminalul

Pornește VS Code din meniul sistemului. Alege **File → Open Folder** și deschide `/home/bogdan/cloud-lab` pe acest mediu (pe calculatorul tău, alege calea unde ai clonat/creat proiectul). Deschide terminalul integrat din **Terminal → New Terminal**. Terminalul integrat este doar o fereastră de terminal; shell-ul poate fi Bash, zsh sau PowerShell.

## 3. Identifică shell-ul

**Bash/Linux/macOS/Git Bash:**

```bash
echo "$SHELL"
```

**PowerShell:**

```powershell
$PSVersionTable.PSVersion
```

În Bash, `echo` afișează valoarea variabilei `$SHELL`; în PowerShell, expresia afișează versiunea PowerShell. Output-ul poate indica `/bin/bash`, `/bin/zsh` sau versiunea `Major Minor Patch`. Dacă `$SHELL` lipsește, încearcă `ps -p $$ -o comm=` în Linux/macOS ori verifică profilul selectat în VS Code pe Windows.

## 4. Verifică Git

Rulează în oricare shell:

```text
git --version
```

Output-ul așteptat seamănă cu `git version 2.x.y`. Comanda doar afișează versiunea; nu schimbă fișiere. Dacă apare „command not found” sau „not recognized”, instalează Git și redeschide terminalul. Nu necesită privilegii.

## 5. Deschide sau creează proiectul

În acest workspace proiectul există deja. Verifică rădăcina cu `pwd` în Bash ori `Get-Location` în PowerShell. Pentru a crea un director nou, alege **una** dintre variante și înlocuiește calea cu una potrivită:

```bash
mkdir -p "$HOME/cloud-lab-practice" && cd "$HOME/cloud-lab-practice"
```

```powershell
New-Item -ItemType Directory -Path "$HOME\cloud-lab-practice" -Force | Out-Null
Set-Location "$HOME\cloud-lab-practice"
```

`mkdir`/`New-Item` creează directorul; `cd`/`Set-Location` schimbă directorul curent. Prima formă este pentru Bash, a doua pentru PowerShell. Nu șterg date; `-Force` în PowerShell tolerează un director deja existent. Rulează comenzile numai dacă vrei un sandbox separat.

## 6. Inițializează Git

Din rădăcina directorului ales, verifică mai întâi dacă nu este deja repository:

```text
git status
```

Dacă mesajul spune că nu este repository și directorul chiar este sandbox-ul tău, inițializează-l:

```text
git init
```

`init` înseamnă initialize (inițializează). Creează metadatele locale `.git`; nu publică nimic. Așteaptă un mesaj despre repository inițializat sau, în versiunile noi, „Reinitialized existing Git repository”. Nu rula orbește în repository-ul unui proiect existent.

## 7. Creează primul fișier

Deschide VS Code Explorer, apasă **New File**, creează `README.md` și scrie:

```markdown
# Laboratorul meu

Învăț Git pas cu pas.
```

Salvează cu Ctrl+S (Windows/Linux) sau Cmd+S (macOS). Editorul creează un fișier text Markdown; conținutul nu execută comenzi.

## 8. Configurează identitatea și fă commit

Setează numele/emailul doar dacă Git cere identitatea. Acestea devin metadate vizibile în commit-urile create; folosește o adresă potrivită pentru proiect. `--global` afectează toate repository-urile utilizatorului; îl poți omite și configura local în proiect.

```text
git config --global user.name "Numele Tău"
git config --global user.email "adresa@example.com"
```

Apoi, din rădăcina proiectului:

```text
git status
git add README.md
git status
git commit -m "Adaugă README inițial"
```

`status` inspectează; `add` pune fișierul în staging area (zona de pregătire); `commit` salvează un punct în istoricul local. Așteaptă mesajul `[main ...] Adaugă README inițial` (numele ramurii poate diferi) și `1 file changed`. `add` și `commit` modifică metadatele Git, nu trimit nimic online. Nu necesita admin.

## 9. Inspectează istoricul

```text
git log --oneline
```

Vezi o linie cu identificator scurt și mesajul commit-ului. Este o comandă de inspectare, fără modificări. Apasă `q` dacă Git deschide un pager.

## 10. Lansează și folosește Codex

Folosește interfața Codex disponibilă în mediul tău (de exemplu integrarea/editorul sau aplicația configurată). Interfețele și comenzile se pot schimba; verifică documentația oficială pentru versiunea instalată înainte să urmezi instrucțiuni despre flags. Începe cu: „Inspectează fișierele, explică ce ai găsit și propune pașii; nu edita încă.” Înainte de acceptarea unei modificări, cere diff-ul, citește-l și verifică rezultatul. Vezi [fluxul Codex](docs/09-codex-workflow.md).

## Continuă

Urmează [roadmap-ul](LEARNING-ROADMAP.md), citește [prima lecție](docs/01-terminal-basics.md), apoi rezolvă exercițiile. Separă comenzile Bash de PowerShell și folosește repository-uri locale până înțelegi efectele comenzilor.
