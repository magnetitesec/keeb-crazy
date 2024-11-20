# USB Keyboard Threat Model Circa 2023

## Actors

1. Typical user (typist) - This is the person that uses the keyboard.
2. USB user - This includes a variety different attack scenarios. A few examples include; the Administrator of your work computer, malicious code running as a compromised victim, or a web application provided access via WebUSB.

## Expected Use Cases

1. Typical user presses buttons (etc) on the keyboard to interact with the computer it is pluigged into.
2. Typical user uses a web site to configure the key mappings (and more) for their device. This includes macros where a single keystroke can generate a sequence of HID events.
3. Typical user updates the firmware via some mechanism.

## Privilege Levels

1. Physical access
2. USB access
3. Firmware operating environment - full access to the device, including raw flash access etc. Microcontroller environments don't have many facilities available (like virtual memory or paging)

## Attack Scenarios

A USB user manipulates keyboard config via bonafide functionality. For example, assigning macros bound to commonly used keys.
 - Gains: The capability to execute commands on any computer the keyboard is plugged into.

A USB user manipulates keyboard firmware via bonafide functionality. For example, a firmware update facility linked with an application on the user's computer to fetch updates from a cloud service.
 - Gains: Firmware operating environment access (only one side of most split keyboards)

A USB user exploits unintended functionality facilitated by memory saftey problems in the firmware (C for QMK).
 - Gains: Firmware operating environment access (only one side of most split keyboards)

## Mitigations

Require phyiscal interaction to confirm exposing functionality over USB.
 - Maybe? Allow a typical user to configure requiring acknowledgement every time or for the remainder of the power cycle.
Provide clear indicator to the user that the device is in flashing mode or configuration mode.


