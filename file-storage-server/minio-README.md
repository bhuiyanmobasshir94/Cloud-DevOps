### Permissions for Minio 
If port for minio is being used or any other minio instance is used 
```
sudo pgrep minio
```
kill that process like this 
```
sudo pkill -9 minio
```
If Minio persistant ./data file has no background write permission 
```
sudo chown -R mobasshir /data && sudo chmod u+rxw /data
```
