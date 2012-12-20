Endgame: Singularity Advanced Research (Extended Soundtrack)

This is a git submodule of Singularity main repository found at:

http://code.google.com/p/endgame-singularity
https://github.com/singularity/singularity

These are the lossless FLAC files created from the Psycle .psy source files
used to generate the Ogg Vorbis files found in the singularity-music package.


To generate your own Ogg Vorbis files from these, use oggenc. The default -q 3
setting was used (averages on ~112kpbs). Also, for normalized loudness, it is
highly recommended to use a pre-processor to apply the ReplayGain values to the
sound data itself, not to Ogg Vorbis tags, since pygame module used by E:S to
play music ignores ReplayGain tags.

On Linux, this can be achieved by:
flac --apply-replaygain-which-is-not-lossless=tn1 --decode *.flac
oggenc *.wav
rm *.wav

However, this will not copy over the tags. If you wish to manually do so, don't
forget to either *not* copy over the replaygain tags, or to recalculate them
afterwards.

On Windows, foobar2000 player can do the conversion, tagging and RG processing.
Use the following Convertion settings:
- Output Format: Ogg Vorbis, q3.0
- Processing: ReplayGain source mode 'track', processing 'apply gain'


As a side note, the scanner used to calculate the ReplayGain values present in
the FLAC files was the modern EBU R128, not the traditional RG scanner. So
expect different gain values if you recalculate or compare using vorbisgain or
similar scanners. However, apart from gain values both methods generate
the same tags and gains are applied in the same manner.
