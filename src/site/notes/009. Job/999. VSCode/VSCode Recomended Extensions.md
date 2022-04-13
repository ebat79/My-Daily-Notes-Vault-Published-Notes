---
{"dg-publish":true,"permalink":"/009-job/999-vs-code/vs-code-recomended-extensions/"}
---
Status:: #State/Develop

## Estensioni consigliate
Per ulteriori informazioni in merito alle singole estensioni consiglio di vedere l'url collegato e la pagina github collegata all'estensione stessa.
Se l'estensione ha qualcosa che non va o si vorrebbero ulteriori implementazioni è possibile aprire una *Issues* nella pagina Github del progetto relativo all'estensione stessa. Io l'ho già fatto in passato ad esempio per l'estensione [[009. Job/999. VSCode/VSCode Recomended Extensions#COBOL|#COBOL]] vedi https://github.com/spgennard/vscode_cobol/issues?q=is%3Aissue+author%3Aebat79+
L'autore mi ha risposto e sistemato il problema con un aggiornamento o spiegato come operare per risolvere il mio problema.

### COBOL 
- Autore: Bitlang
- Url: https://marketplace.visualstudio.com/items?itemName=bitlang.cobol
Ha molte funzioni utili inerenti il linguaggio COBOL tra cui l'evidenziazione della sintassi, l'inclusione delle copy, la visualizzazione grafica della colonna 80 (etc.), supporto per vari dialetti COBOL, etc.
Impostazioni consigliate (vedi dove reperire alcune [[009. Job/999. VSCode/VSCode Recomended Extensions#Impostazioni consigliate|#Impostazioni consigliate]] più sotto):
- Implementare `"coboleditor.copybookdirs"` con le cartelle contenenti le COPY della workspace.
- Implementare `"coboleditor.copybookexts"` con le estensioni dei files di COPY della workspace.
```json
"coboleditor.copybookexts": [
			"",
			"cpy",
			"CPY",
			"txt",
			"TXT",
			"fd",
			"FD",
			"sl",
			"SL",
			"ws",
			"WS",
			"lk",
			"def"
		]
```
- Implementare `"coboleditor.fileformat"` col formato cobol associato a taluni files (es. `"sourceformat": "fixed"` per i sorgenti cobol *tipo Senigallia* cioè che partono dalla ottava colonna e `"sourceformat": "terminal"` per i sorgenti *tipo Rimini* che partono dalla 1 colonna.)
```json
"coboleditor.fileformat": [
			{
				"pattern": "s/*.cbl",
				"sourceformat": "fixed"
			},
			{
				"pattern": "iscbl/*.cbl",
				"sourceformat": "terminal"
			},
			{
				"pattern": "isvid/*.cbl",
				"sourceformat": "terminal"
			},
			{
				"pattern": "cblnocpf/*.cbl",
				"sourceformat": "terminal"
			}
		]
```
- Implementare `"coboleditor.parse_copybooks_for_references": true` per far caricare anche il codice presente nelle copy del sorgente attualmente in modifica.
- Implementare `"coboleditor.program_extensions"` con le estensioni dei programmi cobol. Es.:
```json
"coboleditor.program_extensions": [
			"cob",
			"COB",
			"cbl",
			"CBL",
			"cobol",
			"scbl",
			"pco",
			"list",
			"lst"
		]
```

### Custom AcuCOBOL
- Autore: Enrico Battiston
- Url: https://marketplace.visualstudio.com/items?itemName=EnricoBattiston.custom-acucobol-vscode
Aggiunge all'estensione [[009. Job/999. VSCode/VSCode Recomended Extensions#COBOL|#COBOL]] l'evidenziazione dei commenti `$IF TOTEMX DEFINED`, `$IF XLSCX DEFINED` e `$END`.

### SVN
- Autore: Chris Johnston
- Url: https://marketplace.visualstudio.com/items?itemName=johnstoncode.svn-scm
Aggiunge le funzionalità di SVN a Visual Studio Code.
Verificare che `C:\Program Files\TortoiseSVN\bin` sia disponibile nel `PATH`.

### SVN Gutter
- Autore: beaugust
- Url: https://marketplace.visualstudio.com/items?itemName=beaugust.blamer-vs
Permette di eseguire l'*SVN Blame* all'interno di Visual Studio Code.

### Trailing Spaces
- Autore: Shardul Mahadik
- Url: https://marketplace.visualstudio.com/items?itemName=shardulm94.trailing-spaces
Evidenzia gli spazi alla fine della riga e permette di toglierli con una funzione dedicata.

### PrintCode
- Autore: nobuhito
- Url: https://marketplace.visualstudio.com/items?itemName=nobuhito.printcode
Permette di stampare i sorgenti direttamente da Visual Studio Code mantenendo la colorazione della sintassi.

### Unsaved Files 
- Autore: wraith13
- Url: https://marketplace.visualstudio.com/items?itemName=wraith13.unsaved-files-vscode
Permette di vedere facilmente quali sono i files non salvati.
Utile in caso sia disabilitata l'opzione di salvataggio automatico dei files.

### Peacock
- Autore: John Papa
- Url: https://marketplace.visualstudio.com/items?itemName=johnpapa.vscode-peacock
Permette di cambiare il colore della finestra di Visual Studio Code in base alla Workspace.
Io lo uso impostando le workspace:
- 730: Finestra verde 
- Redditi: Finestra azzurra
- ws-atf: Finestra arancione
In questo modo a colpo d'occhio so dove sto lavorando.

### FreeMarker
- Autore: Daniel Cortes
- Url: https://marketplace.visualstudio.com/items?itemName=dcortes92.FreeMarker
Permette di avere l'evidenziazione del formato FreeMarker utilizzato per scrivere i template sfruttati dal nostro plugin Artiflex.

### Rainbow CSV 
- Autore: mechatroner
- Url: https://marketplace.visualstudio.com/items?itemName=mechatroner.rainbow-csv
Quando si visualizzano file CSV, colora ogni colonna con un colore diverso.
Estende le funzionalità di visualizzazione e interrogazione di files CSV.

### Project Manager
- Autore: Alessandro Fragnani
- Url: https://marketplace.visualstudio.com/items?itemName=alefragnani.project-manager
Permette di organizzare i propri workspace, averne un riepilogo in una finestra laterale, fare lo switch da uno all'altro molto velocemente.

## Impostazioni consigliate
Per crearsi delle impostazioni personalizzate consiglio di crearsi una workspace per ogni ambiente di sviluppo. Io me ne sono creata una per `ws-red\2022`, un'altra per `ws-red\2021`, una per `ws-atf`, un'altra per `LS_MOD730\2022`, etc.
Vedi ad esempio: `w:\gisdoc\enrico\vscode\ws-red2022.code-workspace`.
Vedi ad esempio: `w:\gisdoc\enrico\vscode\vscode7302022.code-workspace`.
A livello globale consiglio:
- Implementare `"files.encoding": "windows1252"` perché attualmente noi creiamo sorgenti in questo encoding (anche se in eclipse in realtà scegliamo UTF-8). *Appunto mio: Non ho ancora capito il vero motivo per cui c'è ancora questa difformità. Sarebbe opportuno passare tutto a UTF-8 compresi i sorgenti in modo tale da poter gestire i caratteri di altre lingue (vedi il tedesco, etc.).*
- Implementare `"editor.renderWhitespace": "all"` per evidenziare i caratteri di SPAZIO con dei pallini grigi.
- Implementare `"editor.renderControlCharacters": true` per evidenziare ad esempio i caratteri di TABULAZIONE, etc.
- Implementare `"editor.tabSize"` col numero di spazi da inserire quando si preme il tasto *TAB*.
- Implementare `"editor.autoIndent": "full"` per l'indentazione automatica del codice.
- Implementare `"files.defaultLanguage": "ACUCOBOL"` per impostare il linguaggio di evidenziazione di default al formato ACUCOBOL.
- Implementare `"files.associations"` con le associazioni delle estensioni. Es.:
```json
"files.associations": {
			"*.aflx": "ftl",
			"*.txt": "ACUCOBOL",
			"*.cbl": "ACUCOBOL",
			"*.lst": "ACUCOBOL",
			"*.list": "ACUCOBOL",
			"*.sl": "ACUCOBOL",
			"*.fd": "ACUCOBOL",
			"*.ws": "ACUCOBOL",
			"*.cpy": "ACUCOBOL",
			"*.def": "ACUCOBOL",
			"*.lk": "ACUCOBOL"
		}
```
- Per un dato formato si possono personalizzare le impostazioni. Es.:
```json
"[ACUCOBOL]": {
			"editor.insertSpaces": true,
			"editor.guides.indentation": true,
			"files.autoGuessEncoding": false,
			"editor.autoIndent": "full",
			"editor.formatOnType": false,
			"editor.rulers": [
				6,
				7,
				72,
				80
			],
			"editor.detectIndentation": false,
			"editor.wordSeparators": "`~!#$%^&*()=+[{]}\\|;:'\",.<>/?"
		}
```
- Implementare `"files.exclude"` per escludere determinati files o cartelle. Es.:
```json
"files.exclude": {
			"**/.metadata/**": true,
			"**/.vscode_cobol/**": true,
			"**/prec/**": true
		}
```
- Implementare `"files.watcherExclude"` per escludere files o cartelle dal *file watching* di Visula Studio Code. Es.:
```json
"files.watcherExclude": {
			"**/.svn/pristine/**": true,
			"**/prec/**": true
		}
```
---
*Riferimenti*

---
*Note veloci*

---
Daily Note: [[002. Diary/001. Daily Notes/2022-04-13|2022-04-13]]
