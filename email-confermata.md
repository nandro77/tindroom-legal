---
title: Email confermata
lang: it
noindex: true
---

<div id="esito-ok" markdown="1">

# Indirizzo confermato

Il tuo indirizzo email è confermato. **Torna nell’app Tindroom e accedi** con la tua email e la tua password.

</div>

<div id="esito-errore" markdown="1" hidden>

# Il link non è più valido

Forse è scaduto, oppure è già stato usato.

Apri l’app Tindroom e accedi con la tua email e la tua password. Se l’indirizzo è già confermato entri normalmente; altrimenti l’app ti porta a **Controlla la tua email**, dove puoi farti mandare un nuovo link.

</div>

Hai bisogno di aiuto? Scrivi all’[assistenza](assistenza.md).

<script>
  // Il link di conferma arriva qui con l'esito nell'indirizzo: i codici di
  // accesso (#access_token=…) se è riuscita, #error=… se il link è scaduto o
  // già usato. Si guarda solo se c'è un errore, poi l'indirizzo si ripulisce:
  // i codici non restano nella barra né nella cronologia del browser.
  (function () {
    function aggiorna() {
      if (!location.hash && !location.search) return;
      var dati = location.hash.slice(1) + '&' + location.search.slice(1);
      var errore = /(^|&)error(_code)?=/.test(dati);
      document.getElementById('esito-ok').hidden = errore;
      document.getElementById('esito-errore').hidden = !errore;
      history.replaceState(null, '', location.pathname);
    }
    aggiorna();
    // Un secondo link aperto nella stessa scheda cambia solo la parte dopo
    // «#»: la pagina non si ricarica, e resterebbe l'esito del primo.
    window.addEventListener('hashchange', aggiorna);
  })();
</script>
