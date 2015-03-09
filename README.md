Docker provisioning sample
=====

Abstract
---

- Building dev servers on local machine
- Virtual Box + Core OS + Docker + Debian container (Redis, MySQL, Postfix)
- Used VirtualBox's docker provisioning system to manage docker container lifesycle.



Initial setup
---

Download coreos image.

```
vagrant box add http://stable.release.core-os.net/amd64-usr/current/coreos_production_vagrant_vmware_fusion.json
```

Hit `vagrant box update` to update the core os image.


Start
---

- The first time will take around 5 minutes depends on the network bandwidth, disk speed and CPU capability.
- The VM will ready for 30 seconds after the second time.

```
vagrant up
```


Halt
---



```
vagrant halt
```


