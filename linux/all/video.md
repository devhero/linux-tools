https://paulherron.com/blog/forcing_keyframes_with_ffmpeg

### Forcing keyframes with an ffmpeg expression

    ffmpeg -i in.mp4 -force_key_frames "expr:gte(t,n_forced*10)" out.mp4