# ASUS Z790 Hero – Continuation from 12-19-2025-z790-hero-memory-post-issue log

## Hardware
- Motherboard: ASUS Z790 Hero
- CPU: Intel i9-14900K
- CPU cooler: Noctua NH-U9S 46.44 CFM
- RAM: G.Skill Trident Z5 RGB 96 GB (2 × 48 GB) DDR5-6800 CL34
- Storage: NVMe drives (removed during testing)
- BIOS version: 3001 x64
- Displays: Multiple monitors tested

## POST / Q-Code Observations
- Code `98`: Console input devices connect
- Code `D7`: No Console Input Devices are found
- Code `B4`: USB hot plug
- Code `A9`: Start of Setup

## Steps Taken
1. Removed all USB devices
2. Removed all NVMe drives
3. Resetting CMOS battery by holding `Clear CMOS` button for 15 seconds and removing then reinstall the battery after 5 minutes
   - System hang on boot and code `98`
5. Tested single RAM module:
   - DIMM_A2 => System hang on boot and code `98`
   - Moving RAM from DIMM_A2 to DIMM_B2 => System hang on boot and code `D7`
   - Moving RAM back to DIMM_A2 => System hang on boot and code `D7`
6. Based on external report, attempted blind BIOS input:
   - Pressed `F10` => POST code changed to `B4`
   - Pressed `F1` => POST code changed to `A9`
7. Switched to a different monitor
8. Video signal appeared and BIOS became visible

- ## Observations
- System was entering BIOS without producing video output
- POST code `A9` confirms BIOS setup mode
- Initial monitor failed to display UEFI output
  - Samsung S32A700NWN => black screen
- Switching monitors immediately resolved the issue
  - Acer XF270H => static + signal drop
  - MSI G272QPF E2 => works perfectly
- BIOS version already supports 14th-gen CPUs
- CPU idle temperature (~50 °C) is elevated but not critical at POST

## Root Cause
- Display initialization / monitor handshake issue during UEFI POST
- BIOS output active but not visible on initial display

## Outcome
- Issue resolved by switching to a different monitor
- System successfully enters BIOS and proceeds past POST

## Note
- Updating motherboard to the latest BIOS might fix the display bug

## References
- ASUS community discussion on POST code 98 behavior:
  https://www.reddit.com/r/ASUS/comments/11w6sfc/motherboard_stuck_on_code_98/
