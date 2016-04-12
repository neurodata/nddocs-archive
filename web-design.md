we have 4 major "threads":

1. computer science
2. big data curation
3. statistical science
4. applied neuroscience

each "project" within the above 4 threads has commonality within thread

#### computer science (cs)

the list of all projects is available in slide form here: http://docs.neurodata.io/ndintro/cs.htm
and in outline form here: http://docs.neurodata.io/nddocs/cs.html

each cs project typically has the following parts:

- webpage
- code
- documentation
- API
- tutorials
- issues
- manuscript
- benchmarks
- installation/setup
- several "highlights" bullets
- an illustrative image

see here http://docs.neurodata.io/ndintro/cs.html#6 for some examples (slides are either cs projects or outline of slides).
in my head, the webpage would essentially include those slides, although not necessarily organized by slides.


in other words, all the content is ready for the cs part of the webpage, it is just not organized well.
what i'd want is it to be better organized, and designed in a such a way that we could relatively easily add additional projects.
there is not a convenient way to automatically build these, so we'd have to manually update/add as appropriate.

#### big data curation

the list of all bigdata curation projects is here: http://neurodata.io/projects (under publications).

each bigdata project typically has the following parts:

- viz
- graph
- manuscript
- media
- analysis
- tools
- docs
- downloads
- (some beautiful images)
- a 1 sentence description
- license info

in theory, each project stores all the necessary metadata in our database, so, you could grab it with a URL.
for example, the bock11 dataset metadata is available here:
http://openconnecto.me/ocp/ca/bock11/info/

the organization of the projects (though it doesn't matter yet much, but will soon), would be based on modality.
here are the list of modalities: http://neurodata.io/#browse (there are only 6).
which modality would be included in the metadata as well.

in other words, for this part, to get everything together and have it automatically updated and stuff, 
would take a bit of web-development, rather than merely web-design.
but of course, we could incorporate web-development stuff as we ramp up, and start very simply.



