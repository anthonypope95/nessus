# Aggiornamento sonde Nessus tramite script

### Linguaggio: Python

### Da console: 
>`python ./updateNessus.py -f IPlist.txt -d packageUpdate.tar`

#### Requisiti
- Apposite credenziali per effettuare l'aggiornamento (controllare i permessi dell'utente)
- Controllare che i servizi necessari siano attivi sugli host (SSH)
- Controllare eventualmente le rules dei Firewall

#### Soluzione 

1. Utilizzare servizio SSH
2. Programma MultiThread (controllare il numero di thread perchè può portare a problemi di saturazione della banda)
3. Input dello script: Lista di indirizzi IP (lettura di file di testo) e il pacchetto di aggiornamento {passaggio percorsi file come parametri allo script}
4. Spedizione file di aggiornamento: utilizzare SCP 
5. SCP chiederà le credenziali per effettuare il trasferimento (username e password)
6. Ricezione notifiche di completamento/errori (relativo alla spedizione del file di aggiornamento)
7. Dopo il trasferimento del file di aggiornamento, prima dell'installazione dello stesso, deve essere verificato l'hash per essere sicuri che il file non sia stato modificato durante il percorso (verifica di sicurezza)
8. Invio di comandi per avviare l'aggiornamento (tramite SSH)
9. Notificare completamento/errori relativi agli aggiornamenti (bisogna capire anche cosa è andato storto e sopratutto su quale macchina o meglio su quale indirizzo IP) {eventualmente scrivere tutto anche in un file di log da consultare al termine dello script}




#### Alternative

5. Utilizzare un meccanismo di autenticazione basato sull'utilizzo di chiave pubblica e chiave privata 
