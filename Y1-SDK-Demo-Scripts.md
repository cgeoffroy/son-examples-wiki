## Assumptions

* `son-sdk-catalogue` locally running
* `son-cli` installed and workspace configured to use SDK catalogue `cat1`
* `son-emu` installed (or running in Vagrant VM)

## Preparation
```bash
# clone example service projects
git cone git@github.com:sonata-nfv/son-examples.git
```

# Single Snort-based Demo

Video: https://www.youtube.com/watch?v=nj5hTk1LLe4

```bash
cd ~/son-examples/service-projects/sonata-snort-service-emu/
# show contents of descriptors (any editor)
subl .

# publish a descriptor to the SDK catalogue
son-publish --component sources/vnf/snort-vnf/snort-vnfd.yml

# package the example service
son-package --project . -n sonata-snort-service

# start the emulator with a demo topology (execute in emulator VM or second terminal)
cd ~/son-emu
sudo python src/emuvim/examples/sonata_y1_demo_topology_1_w_ls_and_sap.py 

# push the service package to the emulator gatekeeper
son-push http://127.0.0.1:5000 -U target/sonata-snort-service.son

# instantiate the pushed service on the emulator
son-push http://127.0.0.1:5000 -D last

# show some emulator features (execute in emulator VM or second terminal)
containernet> nodes
containernet> links
containernet> snort_vnf ifconfig
containernet> ns_input ping -c4 ns_output
containernet> snort_vnf cat /snort-logs/200.0.0.1/ICMP_ECHO

# show snort alerts and how we can directly interact with a container (third terminal)
docker exec -it mn.snort_vnf /bin/bash
tail -f /snort-logs/alert

# generate a alert with a SSH connection 

# show that our snort rules only detect SSH on tcp:22

# reconfigure snort to detect SSH on all ports using DPI functionalities




```


# FW and Snort-based Demo

# FW and vTC-based Demo
TBD. VNFs not ready yet.