# Store Docker Data on different storage

To prevent your 10GB root running full, use a different location like second ssd. 
Stop Docker `systemctl stop docker`
Prepare the SSD with partition, and formating, then rsync the `/var/lib/docker/` to your new path like `/mnt/d/docker`, do the same thing for containerd!

`/etc/docker/daemon.json` should set the `data-root`
```
{
  "data-root": "/mnt/d/docker",
  "features": {
    "containerd-snapshotter": true
  }
}
```

Also think about containerd:

`/etc/containerd/config.toml` should look like:
```
root = "/mnt/d/containerd"
```
