# Core Keeper 1.2.0.4 – load / shader-cache logs (Linux Native + Proton)

Each file below is a single run, captured under a specific condition.

## Native Linux (CoreKeeper Linux build)

- **[Player - load completed.log](./Player%20-%20load%20completed.log)**  
  Baseline “good” run: reaches `Data blocks finished loading from addressables` and continues into manager initialization (load completes).  
  Raw: https://raw.githubusercontent.com/qjv/ck-1.2.0.4-loadbug-logs/main/Player%20-%20load%20completed.log

- **[Player - increased jobs to 11.log](./Player%20-%20increased%20jobs%20to%2011.log)**  
  Same as baseline, but launched with `-job-worker-count 11`; reaches `Data blocks finished...` and later logs `Unrecognized thread niceness after calling setpriority` (priority/renice mismatch warning).  
  Raw: https://raw.githubusercontent.com/qjv/ck-1.2.0.4-loadbug-logs/main/Player%20-%20increased%20jobs%20to%2011.log

- **[Player - opengl.log](./Player%20-%20opengl.log)**  
  Forced OpenGL (`-force-glcore`). Loads past `Data blocks finished...` but logs a format fallback: `'R8_SRGB' is not supported` (RenderTexture fallback warning).  
  Raw: https://raw.githubusercontent.com/qjv/ck-1.2.0.4-loadbug-logs/main/Player%20-%20opengl.log

- **[Player - after load but before closing.log](./Player%20-%20after%20load%20but%20before%20closing.log)**  
  Native Linux run captured right after reaching “loaded” state (pre-quit snapshot).  
  Raw: https://raw.githubusercontent.com/qjv/ck-1.2.0.4-loadbug-logs/main/Player%20-%20after%20load%20but%20before%20closing.log

- **[Player - after load but before closing 2.log](./Player%20-%20after%20load%20but%20before%20closing%202.log)**  
  Same intent as above: another “loaded, before quitting” snapshot.  
  Raw: https://raw.githubusercontent.com/qjv/ck-1.2.0.4-loadbug-logs/main/Player%20-%20after%20load%20but%20before%20closing%202.log

- **[Player - closing after "after load but before closing".log](./Player%20-%20closing%20after%20%22after%20load%20but%20before%20closing%22.log)**  
  Native Linux run showing shutdown path (`Got quit request` / quit handlers).  
  Raw: https://raw.githubusercontent.com/qjv/ck-1.2.0.4-loadbug-logs/main/Player%20-%20closing%20after%20%22after%20load%20but%20before%20closing%22.log

## Proton (Windows build via Steam Play)

- **[Player - Proton Experimental - On Loading.log](./Player%20-%20Proton%20Experimental%20-%20On%20Loading.log)**  
  Proton (D3D11, `Z:\...` paths). Gets to `Initialize global manager` → `Loading data blocks...` and stops there (stuck at the “Loading data blocks…” stage).  
  Raw: https://raw.githubusercontent.com/qjv/ck-1.2.0.4-loadbug-logs/main/Player%20-%20Proton%20Experimental%20-%20On%20Loading.log

- **[Player - Proton Experimental - After Loading.log](./Player%20-%20Proton%20Experimental%20-%20After%20Loading.log)**  
  Proton run that does pass the same stage: reaches `Data blocks finished loading from addressables ...` and continues through initialization (post-load snapshot).  
  Raw: https://raw.githubusercontent.com/qjv/ck-1.2.0.4-loadbug-logs/main/Player%20-%20Proton%20Experimental%20-%20After%20Loading.log
