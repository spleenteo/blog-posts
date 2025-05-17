# 🛠 Git Setup: Vault Privato + Pubblicazione Sottocartella

Questo file documenta la configurazione Git per mantenere il mio vault Obsidian in un repository privato e pubblicare **solo la sottocartella `Spleenteo Blog`** in un secondo repository pubblico tramite `git subtree`.

---
## 📁 Struttura

- **Vault Obsidian:** `~/Documents/Obsidian Vault`
- **Sottocartella da pubblicare:** `Spleenteo Blog`
- **Repo privato (gestito dal plugin Git di Obsidian):** es. `origin`
- **Repo pubblico separato:** `git@github.com:spleenteo/blog-posts.git`

---
## ⚙️ Setup su una nuova macchina

### 1. Clonare il vault privato

```bash
git clone git@github.com:spleenteo/tuo-repo-privato.git "~/Documents/Obsidian Vault"
cd "~/Documents/Obsidian Vault"
```

Sostituire tuo-repo-privato.git con l’URL reale del repository privato.

### **2. Aggiungere il remote del repository pubblico**

    git remote add blog-public git@github.com:spleenteo/blog-posts.git

### **3. Push della sottocartella**  Spleenteo Blog **(con forzatura)**

    git push blog-public $(git subtree split --prefix="Spleenteo Blog" main):main --force

> ⚠️ Sovrascrive il branch main del repo pubblico con il contenuto della sottocartella.

## **💻 Alias di shell (facoltativo)**

    alias :blog='cd "~/Documents/Obsidian Vault" && git push blog-public $(git subtree split --prefix="Spleenteo Blog" main):main --force'

## **✅ Sicurezza**

- Solo la cartella Spleenteo Blog viene pubblicata.
- Mai usare git push blog-public da solo: può pubblicare l’intero vault per errore.
- L’alias :blog è l’unico modo sicuro per pubblicare.

#backup #git #osx