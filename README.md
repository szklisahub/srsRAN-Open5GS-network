# srsRAN-Open5GS-practice1
Configured a network with srsRAN and Open5GS,
referring to a sample config: https://github.com/s5uishida/open5gs_5gc_srsran_sample_config?tab=readme-ov-file#changes_ran

# Changes in each directory:
open5gs/
- amf.yaml, smf.yaml, upf.yaml: mainly IP addresses are changed. (Please look at Vagrantfile to find the IP address allocation for VM.)

srsran/gnb/
- CMakeLists.txt: option(AUTO_DETECT_ISA) should be set to "OFF" to make it compatible with virtualbox.)
- gnb_zmq.yaml: Imainly IP addresses are changed.

srsran/ue/
