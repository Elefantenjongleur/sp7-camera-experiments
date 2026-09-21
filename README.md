# Surface Pro 7 camera experiments

Experimental Surface Pro 7 camera work around IPU4, libcamera, PipeWire
and autofocus.

This is a personal spare-time development setup, not a packaged camera
driver or an upstream-ready patch set.

Development has been done interactively with AI assistance (ChatGPT).
All claimed working behaviour has been compiled and tested on an actual
Surface Pro 7 model 1866.

## Currently demonstrated on the rear OV8865

Working development path:

    OV8865
      -> IPU4
      -> libcamera SimplePipeline
      -> Software ISP
      -> PipeWire / WirePlumber
      -> GNOME Snapshot

The setup also contains experimental DW9719 lens control through
libcamera/IPA and contrast-detection autofocus.

## Native PipeWire

The `pipewire/` directory contains the WirePlumber configuration from
the working development machine.

A temporary workaround disables WirePlumber's V4L2 camera monitor so
that the many raw IPU4 V4L2 nodes are not exposed as individual desktop
cameras.

This is not intended as a final generic configuration because it also
hides ordinary V4L2 webcams.

The locally built SPA-libcamera binary is deliberately not included.
Its exact build path is documented instead.

## libcamera

`libcamera/libcamera-working-tree.patch` is a snapshot of the current
experimental libcamera working tree.

It is provided for technical comparison, not as a clean upstream patch
series.

## Current limitations

- autofocus is still experimental
- AE/AGC is unfinished
- AWB / colour calibration is unfinished
- OV8865 tuning still needs work
- front OV5693 work is currently postponed
- IR OV7251 is not currently a priority

## Current-kernel warning

The diagnostic files in this snapshot may have been generated while
booted into the normal linux-surface kernel rather than the experimental
IPU4 camera kernel.

For that reason the current live PipeWire graph is not used as proof of
the working camera state.
