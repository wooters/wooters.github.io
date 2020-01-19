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

It appears to run about 2x faster than real-time on my macbook pro.

## Example
Running the above `curl` command using:

- audio: [10 seconds of the Gettysburg address](https://www2.cs.uic.edu/~i101/SoundFiles/gettysburg10.wav) from https://www2.cs.uic.edu/~i101/SoundFiles/
- transcript: `four score and sever years ago our fathers brought forth on this continent a new nation conceived in liberty and dedicated to the proposition that all men are created equal`

Output:
```
{
  "transcript": "four score and seven years ago our fathers brought forth on this continent a new nation conceived in liberty and dedicated to the proposition that all men are created equal\n",
  "words": [
    {
      "alignedWord": "four",
      "case": "success",
      "end": 0.71,
      "endOffset": 4,
      "phones": [
        {
          "duration": 0.15,
          "phone": "f_B"
        },
        {
          "duration": 0.13,
          "phone": "ao_I"
        },
        {
          "duration": 0.1,
          "phone": "r_E"
        }
      ],
      "start": 0.33,
      "startOffset": 0,
      "word": "four"
    },
    {
      "alignedWord": "score",
      "case": "success",
      "end": 1.1099999999999999,
      "endOffset": 10,
      "phones": [
        {
          "duration": 0.1,
          "phone": "s_B"
        },
        {
          "duration": 0.07,
          "phone": "k_I"
        },
        {
          "duration": 0.17,
          "phone": "ao_I"
        },
        {
          "duration": 0.06,
          "phone": "r_E"
        }
      ],
      "start": 0.71,
      "startOffset": 5,
      "word": "score"
    },
    
    ...
    
  ]
}
```
