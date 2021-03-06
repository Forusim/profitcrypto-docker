<img src="https://profitcrypto.net/wp-content/uploads/2022/03/profit-300x300.png" width="100">

# Profitcrypto Docker Container
https://profitcrypto.net/

## Configuration
Required configuration:
* Publish network port via `-p 48444:48444`
* Bind mounting a host plot dir in the container to `/plots`  (e.g. `-v /path/to/hdd/storage/:/plots`)
* Bind mounting a host config dir in the container to `/root/.profit`  (e.g. `-v /path/to/storage/:/root/.profit`)
* Bind mounting a host config dir in the container to `/root/.profit_keys`  (e.g. `-v /path/to/storage/:/root/.profit_keys`)
* Set initial `profit keys add` method:
  * Manual input from docker shell via `-e KEYS=type` (recommended)
  * Copy from existing farmer via `-e KEYS=copy` and `-e CA=/path/to/mainnet/config/ssl/ca/` 
  * Add key from mnemonic text file via `-e KEYS=/path/to/mnemonic.txt`
  * Generate new keys (default)

Optional configuration:
* Pass multiple plot directories via PATH-style colon-separated directories (.e.g. `-e plots_dir=/plots/01:/plots/02:/plots/03`)
* Set desired time zone via environment (e.g. `-e TZ=Europe/Berlin`)

On first start with recommended `-e KEYS=type`:
* Open docker shell `docker exec -it <containerid> sh`
* Enter `profit keys add`
* Paste space-separated mnemonic words
* Restart docker cotainer
* Enter `profit wallet show`
* Press `S` to skip restore from backup

## Operation
* Open docker shell `docker exec -it <containerid> sh`
* Check synchronization `profit show -s -c`
* Check farming `profit farm summary`
* Check balance `profit wallet show` 
