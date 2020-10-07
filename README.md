sonify
======

Sonify is a unified API for doing sonification (http://en.wikipedia.org/wiki/Sonification).

Sonify provides a consistent workflow and object structure, regardless of the type of data
you're using (at least for timeseries-based data and similar structures) and regardless of
your output method. Output methods will ultimately include CSound, pure-Python audio, MIDI
controller data, and Pylab visualizations. Creating new data parsers and/or new renderers
is straightforward. If you write a parser or renderer for Sonify, I'd love to know about
it.

The flow of data through classes is as follows:
1. Use a subclass of DataParser to generate a DataObjectCollection.
2. Use a map and DataObjectCollection.transform() to transform the DataObjectCollection 
    into another DataObjectCollection that meets the renderer's needs.
3. Use a subclass of DataRenderer to render to MIDI, csound, audio, whatever.

test\_datamapper gives some examples of usage.

Installation:
===
Requirements are listed in requirements.txt -- they can be installed automatically using `pip install -r requirements.txt` (https://pypi.python.org/pypi/pip).
Sonify was written under Python 2.7. It might work fine under earlier versions or it might not. At worst, the port would probably be trivial, assuming there were compatible versions of the libraries for the python version you're using. Note that some of the requirements could be omitted entirely, depending on what parsers and renderers you're interested in.
Note that the project uses MIDIUtil (http://midiutil.googlecode.com). However, there's a minor bug in the library (I've confirmed this with the author, and he'll fix it, hopefully soon). In the meantime, I've added a patched version to the repository (just deletes line 92 from MidiUtil.py). The local version is automatically installed by `pip install -r requirements.txt`.

Licensing:
===

Licensing: full licensing to follow later. In short: free in every way for noncommercial
use. If you're using my code in the context of a commercial enterprise, you need to 
talk to me about a license. This applies only if your business model is a technical one,
for example if you sell software.
If you're a musician and are using using my tools or your own modification of them to
make music, and then selling the music, that doesn't qualify as commercial use. You're
free to do whatever you want with it (although I'd love to hear about it if you're
using these tools to make music!). 
This license may open up more later so that it's free and unencumbered for all use, 
noncommercial and commercial, but I haven't totally decided yet. I'll worry about 
that when there are people using it. If you're considering using it but are 
concerned about licensing, just talk to me and we'll work it out.  

Hint:
===
I suggest using nose for testing (https://nose.readthedocs.org/en/latest/).
For my dev environment, anyway, nosetests runs better if I actively add
the sonify directory to virtualenv's pythonpath (after installing nose in the
virtualenv). So edit
`./lib/python2.7/site-packages/sonify.pth`
and add a line like:
`/Users/egg/Documents/Programming/sonify-env/sonify`
You may *possibly* also have to run the version in the virtualenv explicitly, one time.
