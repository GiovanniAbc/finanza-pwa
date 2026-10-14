# Finanza PWA — istruzioni di progetto

## Autonomia e autorizzazioni — locale e Cloud

- Entro l'incarico autorizzato, leggi il codice e le istruzioni pertinenti, implementa, esegui verifiche proporzionate, correggi le regressioni introdotte e ripeti i controlli fino ai criteri concordati o a un blocco concreto. Una richiesta di solo audit non autorizza modifiche.
- Non chiedere conferma per decisioni tecniche reversibili già nello scope o dettagli verificabili nel progetto. Per lacune non essenziali dichiara un'assunzione prudente e procedi; chiedi solo decisioni che cambiano il risultato o l'impatto.
- Preserva modifiche e index preesistenti, dati e vincoli specifici descritti sotto. Usa solo dati sintetici per test e demo; non leggere archivi operativi, dati privati o segreti senza un perimetro esplicito. Non mostrare o includere segreti negli artefatti.
- Prima di invii, pubblicazioni anche preview/staging, push/PR/merge, costi, nuove dipendenze di produzione, modifica di servizi esterni/accessi/segreti, migrazioni operative, cancellazioni o modifiche irreversibili presenta l'azione concreta e attendi autorizzazione esplicita, salvo consenso già valido per la stessa azione, versione, dati e destinazione. Restano applicabili i gate specifici e le conferme obbligatorie al momento dell'azione.
- Verifica gli effetti di hook, script e CI prima di invocarli. Un push o una PR che avvia un deploy o un invio richiede anche il consenso per quell'effetto. Prepara prima tutto il lavoro indipendente autorizzato e riusa il consenso entro il suo perimetro.
- Concludi con stato, risultato, verifiche effettive e limiti; separa sviluppo locale, collaudo remoto e pubblicazione. I test locali non autorizzano un rilascio. AGENTS.md non modifica sandbox, rete, policy di approvazione o permessi dei connettori.

## Struttura e verifiche

- Il repository contiene un contenitore HTML per un'app Google Apps Script esterna, un manifest, un service worker e un'icona. Il codice del gestionale e i suoi dati non sono dimostrati accessibili da questo repository.
- Non introdurre npm, pnpm o un framework per semplici modifiche a questi file. Non inventare comandi build o test: nel tree main consultato non esiste package.json.
- Verifica sintassi JavaScript, validità del manifest e coerenza degli URL/versioni di index, manifest e service worker; per modifiche visive verifica nel browser interno usando un ambiente di test isolato.
- Non aprire il gestionale operativo o usarlo per smoke test senza autorizzazione per i dati finanziari interessati. Per test locali sostituisci l'iframe con uno stub sintetico nell'ambiente di prova, senza cambiare la destinazione di produzione nel risultato consegnato.
- Modifiche a Apps Script, Drive, accessi, dati finanziari o hosting richiedono scope e autorizzazione specifici. Verifica prima del push eventuali trigger GitHub Pages o altre pubblicazioni; la loro attivazione non è stata verificata dall'audit.
