IndoWings Streamer - Option B (RTMP + RTSP + SRT-ready)
-------------------------------------------------------

What this starter includes:
- Settings for bitrate, fps, resolution, codec (H.264/H.265)
- Auto-reconnect logic (exponential backoff) in StreamManager
- Stream logs UI (RecyclerView) and log hooks
- Local-recording stubs using MediaMuxer (you must implement encoder-to-muxer wiring)
- RTMP + RTSP support via PedroSG94's rtmp-rtsp-stream-client-java
- SRT is listed as a feature but requires native SDK or prebuilt .so; StreamManager contains stubs.

Important implementation notes:
- Pedro's library covers RTMP and RTSP in many builds; SRT support is less common and usually requires additional
  native components. To enable SRT you can:
  1) Use a prebuilt SRT native client with JNI wrappers (not included).
  2) Integrate a commercial SDK that supports SRT.
  3) Build srt library for Android and expose JNI APIs.

- Local recording (save while streaming): this starter creates MediaMuxer stubs, but you must route encoded audio/video
  output into MediaMuxer tracks. If you use the Pedro library internal encoders, you may need to capture encoder output
  or use a separate encoder pipeline.

Build & run:
1) Open project in Android Studio.
2) Ensure you have internet (Gradle will download jitpack/pedro library).
3) Sync Gradle, fix any method signature mismatches per the library version (check Pedro's repo examples).
4) Connect a real Android device and run.

Next possible upgrades (pick one):
- Implement microphone audio capture and mux audio+video into the stream and file.
- Add orientation-change handling and rotation correction.
- Implement an actual SRT example if you can provide an SRT client dependency or allow me to include a sample native lib.

Tell me which upgrade you want and I'll implement it.
