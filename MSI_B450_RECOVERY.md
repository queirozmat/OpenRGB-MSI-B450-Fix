# MSI B450 Tomahawk lightweight recovery build

This branch is based on OpenRGB `release_candidate_1.0rc2wr0`, the WinRing0
release that detects the MSI B450 Tomahawk (MS-7C02) on the target Windows
system.

The stock MSI-RGB driver configures the Super I/O RGB logical device only when
the controller object is constructed. A full device rescan reconstructs the
object and restores physical color updates, but global rescans notify and can
destabilize SignalRGB while it is loading plugins.

For MS-7C02 only, this branch repeats the existing MSI-RGB initialization
sequence every 30 seconds when color traffic is active. It does not enumerate
devices, change the SDK device list, restart SignalRGB, or run a background
polling thread. Other MSI-RGB boards keep the original behavior.
