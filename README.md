# click2callPlayground
This is a Javascript playground for experimenting with synthesizing call-like signals from clicks

The overall plan is to synthesize 'click' like signals at a high sampling rate (1 million samples per second).
Then, lowpass filter and resample to our 'normal' orcasound sampling rate range (< 48 kilo samples per second))
And, listen to the synthesized signal and observe the power spectral density and a spectrogram of the synthesized signal.
