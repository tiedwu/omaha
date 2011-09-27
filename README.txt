RELEASE NOTES
-------------------------------------------------------------------------------
zgb-factory_bundle-mp_0.13.587.135_20110923_rc6

ChromeOS:     0.13.587.135 x86-zgb/x86-zgb-he MP-v2 keys
Factory Test: 0.15.980.13 x86-zgb (unsigned)
Factory Shim: 0.15.980.5 x86-zgb (MP signed)
Firmware:     ZGB.03.61.0740.0062G7 (MP signed)
EC Firmware:  ZGB_EC_100.bin

Changes in factory test image:
 - issue 6066: [zgb] hdmi doest' work on RC4 factory image

-------------------------------------------------------------------------------
zgb-factory_bundle-mp_0.13.587.135_20110919_rc5

ChromeOS:     0.13.587.135 x86-zgb/x86-zgb-he MP-v2 keys
Factory Test: 0.15.980.5 x86-zgb (unsigned)
Factory Shim: 0.15.980.5 x86-zgb (MP signed)
Firmware:     ZGB.03.61.0740.0062G7 (MP signed)
EC Firmware:  ZGB_EC_100.bin

Image files are the same as previous RC3.

Bundle content:
 - Fixed error in make_factory_config.sh
 - Moved configuration files into "config" folder.
   Please run "scripts/make_factory_config.sh --config config/mp_factory.conf"

-------------------------------------------------------------------------------
zgb-factory_bundle-mp_0.13.587.135_20110917_rc4

ChromeOS:     0.13.587.135 x86-zgb/x86-zgb-he MP-v2 keys
Factory Test: 0.15.980.5 x86-zgb (unsigned)
Factory Shim: 0.15.980.5 x86-zgb (MP signed)
Firmware:     ZGB.03.61.0740.0062G7 (MP signed)
EC Firmware:  ZGB_EC_100.bin

Image files are the same as previous RC3.

Bundle content:
 - Added mini-omaha server and factory setup scripts.
   Now you don't need to "repo sync" just for setting up mini-omaha server.
   Just extract the bundle and then run:

   scripts/make_factory_config.sh --config mp_factory.conf
   cd dev
   python devserver.py --factory_config miniomaha.conf

 - To build RMA shim images:
   scripts/make_factory_config.sh --config rma.conf
   # you'll then have "rma-x86-zgb-he.bin" and "rma-x86-zgb.bin"

-------------------------------------------------------------------------------
zgb-factory_bundle-mp_0.13.587.135_20110917_rc3

ChromeOS:     0.13.587.135 x86-zgb/x86-zgb-he MP-v2 keys
Factory Test: 0.15.980.5 x86-zgb (unsigned)
Factory Shim: 0.15.980.5 x86-zgb (MP signed)
Firmware:     ZGB.03.61.0740.0062G7 (MP signed)
EC Firmware:  ZGB_EC_100.bin

Factory Shim & Test Image Changes:
 - Add pegasus driver (ADMTEK AN8515)

Release Image Changes:
 - Update to 0.13.587.135, the latest R13 FSI candidate

New files:
 - BULID_HOW_TO.txt, providing complete instruction for setting up factory
   branch.

 - mp_factory.conf, rma.conf:
   make_factory_package.sh on factory branch supports a new feature: --config
   No need to type lots of complex commands, just run:
   ~/trunk/src/scripts/make_factory_package.sh --config PATH_TO_BUNDLE/mp_factory.conf
   And then mini-omaha will be configured correctly.

-------------------------------------------------------------------------------
zgb-factory_bundle-mp_0.13.587.134_20110906_rc2
ChromeOS:     0.13.587.134 x86-zgb/x86-zgb-he MP-v2 keys
Factory Test: 0.15.980.2 x86-zgb (unsigned)
Factory Shim: 0.15.980.2 x86-zgb (MP signed)
Firmware:     ZGB.03.61.0740.0062G7 (MP signed)
EC Firmware:  ZGB_EC_100.bin

Factory Test Image Changes:
 - issue crosbug.com/p/5872: tpm_version error (due to disk full)
 - issue crosbug.com/p/5395: always log MEID even if carrier was not set
 - Serial Number is now a required VPD value. See factory_SetSN for example.
 - HDMI is now started by "initctl start chrontel".
 - Move to 0.15.980.B
   This image was built from the new 0.15.980.B factory branch.
   This branch can be built by adding "-b factory-980.B" to the repo init command:
   repo init -u http://git.chromium.org/chromiumos/manifest.git -b factory-980.B
   See HOW_TO_BUILD.txt for more information.

HWID:
 - updated bundle to new MP configurations (DELTA, EPSILON, ZETA)
    ACER ZGB DELTA-DE 6494
    ACER ZGB DELTA-ES 6446
    ACER ZGB DELTA-FR 1131
    ACER ZGB DELTA-GB 0702
    ACER ZGB DELTA-IT 5185
    ACER ZGB DELTA-US-INTL 7354
    ACER ZGB DELTA-US 3919
    ACER ZGB EPSILON-DE 1424
    ACER ZGB EPSILON-ES 0624
    ACER ZGB EPSILON-FR 3269
    ACER ZGB EPSILON-GB 1280
    ACER ZGB EPSILON-IT 2335
    ACER ZGB EPSILON-US-INTL 9303
    ACER ZGB EPSILON-US 7201
    ACER ZGB ZETA-DE 0178
    ACER ZGB ZETA-ES 9362
    ACER ZGB ZETA-FR 6151
    ACER ZGB ZETA-GB 2290
    ACER ZGB ZETA-IT 0285
    ACER ZGB ZETA-US-INTL 2390
    ACER ZGB ZETA-US 5219

To setup mini-omaha server, please type following command:

  # first, setup x86-zgb
  make_factory_package.sh \
   --board x86-zgb \
   --release release/chromeos_0.13.587.134_x86-zgb_recovery_stable-channel_mp-v2.bin \
   --factory factory_test/chromiumos_factory_image.bin \
   --firmware firmware/chromeos-firmwareupdate \
   --hwid hwid_bundle_zgb_mp.sh \
   --detect_release_image

  # next, setup x86-zgb-he
  make_factory_package.sh \
   --subfolder x86-zgb_he \
   --board x86-zgb_he \
   --release release/chromeos_0.13.587.134_x86-zgb-he_recovery_stable-channel_mp-v2.bin \
   --factory factory_test/chromiumos_factory_image.bin \
   --firmware firmware/chromeos-firmwareupdate \
   --hwid hwid/updater_zgb_mp.sh \
   --detect_release_image

-------------------------------------------------------------------------------
zgb-factory_bundle-mp_0.13.587.113_20110816_rc1
ChromeOS:     0.13.587.113 x86-zgb/x86-zgb-he MP-v2 keys
Factory Test: 0.12.369.31 [mod with ToT gooftool/ HWID] x86-zgb (unsigned)
Factory Shim: 0.15.885.0 with MP key (compatible for RMA)
Firmware:     ZGB.03.61.0740.0062G7 (MP signed)
EC Firmware:  ZGB_EC_014.bin

The bundle includes both release images, reference factory test image, install
shim, firmware, and HWID updaters.

To configure mini-omaha server serving both boards, you must first update your
mini-omaha to ToT version (do a fresh checkout, or repo sync then
"sudo emerge crosutils"); remember to using following board names:

  x86-zgb     for gobi
  x86-zgb_he  for non-gobi

(1) configure x86-zgb (normal image with gobi):
make_factory_package.sh \
 --board x86-zgb \
 --release release/chromeos_0.13.587.113_x86-zgb_recovery_stable-channel_mp-v2.bin \
 --factory factory_test/chromiumos_factory_image.bin \
 --firmware firmware/chromeos-firmwareupdate \
 --hwid hwid/updater_zgb_mp.sh \
 --detect_release_image

(2) configure x86-zgb-he (without gobi):
make_factory_package.sh \
 --subfolder x86-zgb_he \
 --board x86-zgb_he \
 --release release/chromeos_0.13.587.113_x86-zgb-he_recovery_stable-channel_mp-v2.bin \
 --factory factory_test/chromiumos_factory_image.bin \
 --firmware firmware/chromeos-firmwareupdate \
 --hwid hwid/updater_zgb_mp.sh \
 --detect_release_image

NOTE: --subfolder currently won't replace previously created configuration - IT
      ALWAYS ONLY APPEND. So everytime you want to update the any of the images
      (or firmware/hwid/... etc), make sure you've executed both the commands
      above - first WITHOUT subfolder and then WITH subfolder.
      Otherwise, you'll get checksum failure when installing images.

===============================================================================
R12 Factory Bundles History
===============================================================================

zgb-mp_20110616_rc9
ChromeOS:     [CHANGED] 0.12.433.115 x86-zgb MP-v2 keys
Factory Test: 0.12.369.31 x86-zgb (unsigned)
Factory Shim: 0.12.369.8, new "Universal shim" with MP/PVT/DEV keys
Firmware:     ZGB.03.61.0740.0062G7 (MP signed)
EC Firmware:  ZGB_EC_014.bin

The only change is release image, updated to 115 for security fix.
Factory test image and firmware are both not changed.

You can manually update only the release image, and re-run
make_factory_package to update mini-omaha server.

-------------------------------------------------------------------------------
zgb-mp_20110609_rc8
ChromeOS:     [CHANGED] 0.12.433.107 x86-zgb MP-v2 keys
Factory Test: [CHANGED] 0.12.369.31 x86-zgb (unsigned)
Factory Shim: 0.12.369.8, new "Universal shim" with MP/PVT/DEV keys
Firmware:     ZGB.03.61.0740.0062G7 (MP signed)
EC Firmware:  [CHANGED] ZGB_EC_014.bin

Factory test image change:
 - Updated 'mosys' to support reading memory size with any kernel
 - HWID component list updated for new EC firmware

-------------------------------------------------------------------------------
zgb-mp_20110601_rc7
ChromeOS:     [CHANGED] 0.12.433.87 x86-zgb MP-v2 keys
Factory Test: [CHANGED] 0.12.369.27 x86-zgb (unsigned) with HWID updates
Factory Shim: 0.12.369.8, new "Universal shim" with MP/PVT/DEV keys
Firmware:     [CHANGED] ZGB.03.61.0740.0062G7 (MP signed)
EC Firmware:  [CHANGED] ZGB_EC_013.bin

Factory test image change:
 - HWID component list updated for new BIOS/EC firmware and touchpad firmware

-------------------------------------------------------------------------------
zgb-mp_20110531_rc6
ChromeOS:     [CHANGED] 0.12.433.76 x86-zgb MP-v2 keys
Factory Test: [MODIFIED] 0.12.369.25 x86-zgb (unsigned) with HWID updates
Factory Shim: 0.12.369.8, new "Universal shim" with MP/PVT/DEV keys
Firmware:     ZGB.03.61.0740.0062G6 (MP signed)
EC Firmware:  ZGB_EC_012.bin

Release image changes:
 - Updated EULA pages

Factory test image change:
 - HWID component list updated for Touchpad Firmware change

-------------------------------------------------------------------------------
zgb-mp_20110530_rc5
ChromeOS:     [CHANGED] 0.12.433.71 x86-zgb MP-v2 keys
Factory Test: [MODIFIED] 0.12.369.25 x86-zgb (unsigned) with HWID updates
Factory Shim: 0.12.369.8, new "Universal shim" with MP/PVT/DEV keys
Firmware:     [CHANGED] ZGB.03.61.0740.0062G6 (MP signed)
EC Firmware:  ZGB_EC_012.bin

This is a release with HWID component lists updated for BIOS 0062G6.

-------------------------------------------------------------------------------
zgb-mp_20110527_rc4
ChromeOS:     [CHANGED] 0.12.433.62 x86-zgb MP keys
Factory Test: [CHANGED] 0.12.369.22 x86-zgb (unsigned) with HWID updates and loc fix
Factory Shim: 0.12.369.8, new "Universal shim" with MP/PVT/DEV keys
Firmware:     [CHANGED] ZGB.03.61.0740.0062G4.fd (MP signed)
EC Firmware:  [CHANGED] ZGB_EC_012.bin

Factory test image changes:
 - "[ZGB] Failed to read EC (in reasonable time) when it's write-protected"
   http://code.google.com/p/chrome-os-partner/issues/detail?id=3668
 - "ZGB: Factory - Displaying other language bitmap instead of English bitmap"
   http://code.google.com/p/chrome-os-partner/issues/detail?id=3868

 New HWID list:
  # ALPHA = WiFi + AUO Panel
  # BETA = WiFi + CMO Panel
  # GAMMA = 3G + CMO Panel
  ACER ZGB ALPHA-DE 1802
  ACER ZGB ALPHA-ES 3786
  ACER ZGB ALPHA-FR 4223
  ACER ZGB ALPHA-GB 7370
  ACER ZGB ALPHA-IT 4645
  ACER ZGB ALPHA-US-INTL 6722
  ACER ZGB ALPHA-US 4443
  ACER ZGB BETA-DE 3227
  ACER ZGB BETA-ES 2795
  ACER ZGB BETA-FR 6478
  ACER ZGB BETA-GB 9131
  ACER ZGB BETA-IT 7076
  ACER ZGB BETA-US-INTL 1108
  ACER ZGB BETA-US 2170
  ACER ZGB GAMMA-DE 5816
  ACER ZGB GAMMA-ES 3400
  ACER ZGB GAMMA-FR 4797
  ACER ZGB GAMMA-GB 1624
  ACER ZGB GAMMA-IT 9655
  ACER ZGB GAMMA-US-INTL 2985
  ACER ZGB GAMMA-US 8585

  # A special "DOGFOOD" HWID is for trying factory process with PVT "3G+AUO"
  # device
  ACER ZGB DOGFOOD 5871

-------------------------------------------------------------------------------
zgb-ramp_20110518_rc3

ChromeOS:     [CHANGED] 0.12.433.46 x86-zgb MP keys
Factory Test: [CHANGED] 0.12.369.16 x86-zgb (unsigned) with HWID updates and BT fix
Factory Shim: [CHANGED] 0.12.369.8, new "Universal shim" with MP/PVT/DEV keys
Firmware:     [CHANGED] ZGB.03.61.0739.0061G1.fd (MP signed)
EC Firmware:  [CHANGED] ZGB_EC_010.bin

Factory test image changes:
 - "ZGB BU12 Compatibility Driver Testing and Patch Changes"
   https://code.google.com/p/chrome-os-partner/issues/detail?id=2752

 - "[zgb] wireless led never light up even connection to AP"
   http://code.google.com/p/chrome-os-partner/issues/detail?id=3872

Factory install shim image changes:
 - Install shim is now bootable for DEV, PVT, MP key devices.
 - To change the mini-omaha server IP in universal install shim:
   1. (in factory_shim folder) ./mount_partition -rw chromeos_*.bin 1 /media
   2. sudo vim /media/dev_image/etc/lsb-factory
   3. sudo umount /media

-------------------------------------------------------------------------------
zgb-ramp_20110511_rc2

ChromeOS:       [CHANGED] 0.12.433.38 x86-zgb MP keys
Factory Test:   [MODIFIED] 0.12.369.13 x86-zgb (unsigned) with HWID updates
Factory Shim:   0.12.369.8 x86-zgb MP keys
Firmware:       [MODIFIED] ZGB.03.61.0738.0060G3.fd (MP signed)
EC Firmware:    ZGB_EC_009.bin

Release image and Firmware change:
 - "60G3: Failed to install developer firmware"
   http://code.google.com/p/chrome-os-partner/issues/detail?id=3722

RAMP HWID has a minor change:
   ACER ZGB RAMP GAMMA-NL 2138 -> ACER ZGB RAMP GAMMA-US-INTL 2534
   (The launch in NL country is actually using US-INTL layout)

-------------------------------------------------------------------------------
zgb-ramp_20110510_rc1

ChromeOS:       0.12.433.37 x86-zgb MP keys
Factory Test:   0.12.369.13 x86-zgb (unsigned) with updated firmware hash
Factory Shim:   0.12.369.8 x86-zgb MP keys
Firmware:       ZGB.03.61.0738.0060G3.fd (MP signed)
EC Firmware:    ZGB_EC_009.bin

 * RAMP HWIDs are now included and replaced PVT HWIDs.
   - Added 3 new keyboard layouts: IT, NL, ES
   ACER ZGB RAMP ALPHA-US 3543
   ACER ZGB RAMP BETA-US 9825
   ACER ZGB RAMP GAMMA-US 5013
   ACER ZGB RAMP GAMMA-DE 0324
   ACER ZGB RAMP GAMMA-ES 2948
   ACER ZGB RAMP GAMMA-FR 0657
   ACER ZGB RAMP GAMMA-IT 9227
   ACER ZGB RAMP GAMMA-NL 2138
   ACER ZGB RAMP GAMMA-UK 2931

Release image changes:
[firmware]
 - "[ZGB] Flashrom should preserve RO VPD data"
   http://code.google.com/p/chrome-os-partner/issues/detail?id=3540

[wiping]
 - "Speed up Factory Wiping"
   http://code.google.com/p/chromium-os/issues/detail?id=14942

Factory test image changes:

[chrontel (HDMI)]
 - "The LCD screen will flash after connected HDMI monitor"
   http://code.google.com/p/chrome-os-partner/issues/detail?id=3011
 - "HDMI EA test, it failed in the EA 7-1 2 & 4 EDID block detect and DVI
    protocol compliance test"
   http://code.google.com/p/chrome-os-partner/issues/detail?id=3177

[WiFi]
 - "WiFi is unable to search AP with new WLAN HB116 card [Card ID: 105b:e04a]"
   http://code.google.com/p/chrome-os-partner/issues/detail?id=3439

[gooftool (Google Required Test)]
 - "Speed up the switching process (wiping) from factory test image to release
    image"
   http://code.google.com/p/chromium-os/issues/detail?id=14139

[backlight]
 - "Make screen always light up"
   http://code.google.com/p/chrome-os-partner/issues/detail?id=2950

-------------------------------------------------------------------------------
zgb-pvt_20110420_rc3

ChromeOS:       0.12.378.0 x86-zgb PVT keys
Factory Test:   [MODIFIED] 0.12.369.6 x86-zgb (unsigned)
Factory Shim:   0.12.369.1 x86-zgb PVT keys (with legacy boot fix)
Firmware:       ZGB.03.61.0734.0055G2.fd (PVT signed)
EC Firmware:    ZGB_EC_005.bin

1. The only changed file is "factory test image",
   /usr/local/autotest/site_tests/hardware_Components/data_x86-zgb/ACER_ZGB_PVT
   which allows second source flash chip Macronix MX25L3206E (ID:MX25L3205)

   All other image files are the same as RC2.

-------------------------------------------------------------------------------
zgb-pvt_20110413_rc2

ChromeOS:       [UPDATED] 0.12.378.0 x86-zgb PVT keys
Factory Test:   [UPDATED] 0.12.369.6 x86-zgb (unsigned)
Factory Shim:   [MODIFIED] 0.12.369.1 x86-zgb PVT keys (with legacy boot fix)
Firmware:       [UPDATED] ZGB.03.61.0734.0055G2.fd (PVT signed)
EC Firmware:    ZGB_EC_005.bin

1. BIOS is updated from 0055 to 0055G2, which is more stable.
   OS image is also updated to contain those firmware.

2. Factory install shim is the same as last H2O-fix version on 04/12
   (factory_install_shim_20110412_H2Ofix.bin.bz2)

3. Factory test image has updated with latest HWID list for ZGB, and updated
   gooftool to support the new HWID list.

   The new list:
   ACER ZGB PVT ALPHA 0527      # No Gobi, for C1/C4
   ACER ZGB PVT BETA 6683       # No Gobi, Second Source, for C2
   ACER ZGB PVT GAMMA 2900      # w/Gobi, for C3
   ACER ZGB PVT GAMMA-UK 0422   # C5
   ACER ZGB PVT GAMMA-FR 8500   # C6
   ACER ZGB PVT GAMMA-DE 9985   # C7

4. To support using HWID on models with different keyboard layout/locale,
   the factory process has to execute following command:

   # UK
   vpd -i RO_VPD -s "keyboard_layout"="xkb:gb:extd:eng"
   vpd -i RO_VPD -s "initial_locale"="en-GB"

   # FR
   vpd -i RO_VPD -s "keyboard_layout"="xkb:fr::fra"
   vpd -i RO_VPD -s "initial_locale"="fr"

   # DE
   vpd -i RO_VPD -s "keyboard_layout"="xkb:de::ger"
   vpd -i RO_VPD -s "initial_locale"="de"

   See https://code.google.com/p/chrome-os-partner/issues/detail?id=3252 for
   more information.

-------------------------------------------------------------------------------
zgb-pvt_20110408_rc1

ChromeOS:       0.12.374 x86-zgb PVT keys
Factory Test:   0.12.369.2 x86-zgb (unsigned)
Factory Shim:   0.12.369.1 x86-zgb PVT keys
Firmware:       ZGB.03.61.0734.0055.fd (PVT signed)
EC Firmware:    ZGB_EC_005.bin

1. This factory package is using images signed by PVT, and is NOT compatible
   with DEV key firmware.

   If you want to use the factory install shim on a ZGB/ZGA which was using ZGA
   PVT key firmware or DEV key (or "unsigned") firmware, you need to manually
   flash your firmware to H2O or PVT H2C first.

   To do that, boot your device and copy firmware/chromeos-firmwareupdate into
   the device (or copy to a bootable image), and then execute:

   sudo sh ./chromeos-firmwareupdate --force --factory

   After reboot, you should be able to use the PVT signed factory install shim.

2. HWID (in factory test image) may be changed before real PVT runs
   Currently included HWIDs are:
   ACER ZGB PVT ALPHA 0527    # No Gobi, for Sku 1/4
   ACER ZGB PVT BETA 6683     # No Gobi, for Sku 2
   ACER ZGB PVT GAMMA 2900    # Include Gobi, for Sku 3

   Note we need following properties to complete the component list:
   Display Panel ID for both Sku 1 and Sku 2 (part_id_display_panel)
   SSD ID (part_id_storage)
   TouchPad ID (vendor_id_touchpad)

   You can run gooftool to get above IDs:
    /usr/local/gooftool/gft_hwcomp.py /usr/local/autotest/site_tests/hardware_Components/approved_components

   And send Google the output messages.

3. Synaptics driver is included: verified by "/opt/Synaptics/bin/syndetect -l"
   Gobi driver is included: verified by existence of /opt/Qualcomm

4. BIOS will be changed to ZGB.03.61.0734.0055G2.fd for real PVT
   (No signed 0055G2 BIOS image yet, so using 0055 for this release)

5. OS release image may be updated before real PVT runs

6. Modification made to original factory test image:
   - updated 'mosys' to latest version
   - included latest HWID definition and bitmaps
