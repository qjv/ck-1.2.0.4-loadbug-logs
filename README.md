# Core Keeper 1.2.0.4 – load / shader-cache logs (Linux Native)

Each file below is a single run, captured at a specific condition.

## Native Linux (CoreKeeper Linux build)

- **Player - load completed.log**  
  Baseline “good” run: reaches `Data blocks finished loading from addressables` and continues into manager initialization (load completes). :contentReference[oaicite:0]{index=0}

- **Player - increased jobs to 11.log**  
  Same as baseline, but launched with `-job-worker-count 11`; reaches `Data blocks finished...` and later logs `Unrecognized thread niceness after calling setpriority` (priority/renice mismatch warning). :contentReference[oaicite:1]{index=1}

- **Player - opengl.log**  
  Forced OpenGL (`-force-glcore`). Loads past `Data blocks finished...` but hits format fallback: `'R8_SRGB' is not supported` (RenderTexture format fallback warning). :contentReference[oaicite:2]{index=2}

- **Player - after load but before closing.log**  
  Native Linux run captured right after reaching “loaded” state (pre-quit snapshot). :contentReference[oaicite:3]{index=3}

- **Player - after load but before closing 2.log**  
  Same intent as above: another “loaded, before quitting” snapshot. :contentReference[oaicite:4]{index=4}

- **Player - closing after "after load but before closing".log**  
  Native Linux run showing shutdown path (`Got quit request` / quit handlers). :contentReference[oaicite:5]{index=5}


## Proton (Windows build via Steam Play)

- **Player - Proton Experimental - On Loading.log**  
  Proton (D3D11, `Z:\...` paths). Gets to `Initialize global manager Loading data blocks...` and stops there (stuck at the “Loading data blocks…” stage). :contentReference[oaicite:6]{index=6}

- **Player - Proton Experimental - After Loading.log**  
  Proton run that *does* pass the same stage: reaches `Data blocks finished loading from addressables ...` and continues through initialization (post-load snapshot). :contentReference[oaicite:7]{index=7}
