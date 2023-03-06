# Nolus-rila snapshot (updated every 12 hours) ~4.5GB


Stop the node and remove db
```
sudo systemctl stop nolusd
cp $HOME/.nolus/data/priv_validator_state.json $HOME/.nolus/priv_validator_state.json.backup
rm -rf $HOME/.nolus/data
```
Download snapshot

```
mkdir $HOME/.nolus/data
wget -O - http://85.10.198.169/nolus/nolus-rila_latest.tar | tar xf - -C $HOME/.nolus/data
mv $HOME/.nolus/priv_validator_state.json.backup $HOME/.nolus/data/priv_validator_state.json
```
Start service
```
sudo systemctl start nolusd && sudo journalctl -u nolusd -f --no-hostname -o cat
```
