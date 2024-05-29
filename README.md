# click2callPlayground
This is a Javascript playground for experimenting with synthesizing call-like signals from clicks

The overall plan is to synthesize 'click-like' signals at a high sampling rate (1 million samples per second).
Then, lowpass filter and resample to our 'normal' orcasound sampling rate range (< 48 kilo samples per second))
And, listen to the synthesized signal and observe the power spectral density and a spectrogram of the synthesized signal.

This page is being served via Github Pagesat https://orcasound.github.io/click2callPlayground/

To run locally, clone the repository and then open a terminal window in your local directory and run a local server from there.

Under Ubuntu: python3 -m http.server --bind 127.0.0.1 9000

Find your program locally at: http://127.0.0.1:9000/index.html

The program is designed as a pipeline which can be entered at a variety of points.  After entry, the pipeline continues to the end.
The Javascript is mostly in the HTML file and is more-or-less in the order of the pipeline calls.

    function runPipeline(iStart){
                if (iStart === 0) {
                    msg.innerHTML = "Calculating clicks ...";
                    buildClicks();
                    plotClicks();
                    msg.innerHTML = "";
                }
                if (iStart <= 1){
                    msg.innerHTML = "Calculating call ...";
                    buildCall();
                //    plotCall();
                    msg.innerHTML = "";
                }
                if (iStart <= 2){
                    msg.innerHTML = "Resampling call ...";
                    window.global_audioSamplerate = parseInt(document.getElementById('Audio samplerate').value);
                    resampleCall();
                    msg.innerHTML = "";
                }
                if (iStart <= 3){
                    msg.innerHTML = "Plotting call ...";
                    plotCall();
                    plotResampledCall();
                    msg.innerHTML = "";
                }
                if (iStart <= 4){
                    msg.innerHTML = "Plotting spectrogram ...";
                    plotSpectrogram();
                    msg.innerHTML = "";
                }
    
            }
Currently, the screen does NOT update via the msg.innerHTML statement.  This is an Issue!
There are more, as well.  Check the Github Issues.
