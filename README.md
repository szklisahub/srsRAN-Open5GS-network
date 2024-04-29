# srsRAN-Open5GS-practice1
Configured a 5G mobile network with srsRAN and Open5GS combined with ZeroMQ,
referring to: https://github.com/s5uishida/open5gs_5gc_srsran_sample_config?tab=readme-ov-file#changes_ran

Changes in configuration files

- Mainly, IP addresses and some settings are changed but primarily follow the sample config. Vagrantfile is written to build 4 VMs for UE, gNB, C-plane, and U-plane. Please look at Vagrantfile to find the IP address allocation.

Changes for particular reasons

- srsran/gnb/CMakeLists.txt: option(AUTO_DETECT_ISA) should be set to "OFF" to make it compatible with virtualbox.

- srsran/ue/nas_5g.cc: Change not to include NSSAI IE in cleartext IEs in Registration Request. Please refer to: https://github.com/srsran/srsRAN_4G/pull/1214/commits/427f1550c4a049835177242fc26fbdd2180e4159
