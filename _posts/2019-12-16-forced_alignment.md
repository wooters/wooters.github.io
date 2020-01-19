# Using the gentle forced aligner

A quick and easy way of aligning orthographic transcripts with audio to get word-level timing information.

## Start the server:
Assumes you have `docker` installed. See [the gentle github repo](https://github.com/lowerquality/gentle) for more info.

```bash
$ docker run -p 8765:8765 lowerquality/gentle
```

## Run forced-alignment from command-line
```bash
$ curl -F "audio=@/path/to/audio.wav" \
  -F "transcript=@/path/to/transcript.txt" \
  "http://localhost:8765/transcriptions?async=false"
```

It looks like it runs about 2x faster than real-time on my macbook pro.
