# fubuki

fubuki è un'implementazione VPN mesh, simile a un semplice strumento di rete come TincVPN

Piattaforme attualmente supportate:

- Windows
- Linux
- macOS

## Principio di funzionamento

Richiede un server di rete pubblica per mantenere la mappatura degli indirizzi dei nodi client. I nodi comunicano tra loro P2P. Quando i nodi non possono comunicare a causa di restrizioni NAT e altri problemi, passeranno ai relè del server.

## Come si usa

[Descrizione del file di configurazione](https://github.com/Giancarlo1974/fubuki/tree/master/cfg-example)
### Pre-dipendenze

#### Windows
Wintun.dll (https://www.wintun.net) deve trovarsi nella stessa directory del file eseguibile o in System32 e può essere eseguito con privilegi di amministratore

#### Linux & macOS
Richiede che il kernel supporti il ​​modulo TUN e sia in grado di funzionare come root

### Comandi client
Avvio del nodo:

```shell
sudo ./fubuki client client-config.json
```
Visualizza le informazioni sul nodo:
```shell
./fubuki info
```
o specificare l'indirizzo API
```shell
./fubuki info "127.0.0.1:1234"
```
### Comandi del server
Avvio del server:
```shell
./fubuki server server-config.json
```

## Generazione di origine
Installa l'ambiente Rust

La toolchain della piattaforma Windows deve essere MSVC
Installazione di Rust su Windows con MSVC Toolchain

Se è necessario abilitare il set di istruzioni AES-NI, aggiungere una variabile di ambiente `RUSTFLAGS="-C target-cpu=native"`
```shell
git clone "https://github.com/xutianyi1999/fubuki";
cd fubuki;
cargo build --release;
```
