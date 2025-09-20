# hackyscripts
Unprofessional but useful scripts, mostly Linux/Bash/Perl. These scripts are Public Domain and are also licenced under MIT.

These scripts are not suitable for production use, they are not widely used nor comprehensively tested. They might accidentally destroy your data. Take backups before using them.

However you might find them useful, either as-is, or as the basis or inspiration for your own customisations or re-writes.

# tvshow-filename-to-nfo
tvshow-filename-to-nfo [ OPTIONS ] [ directory ] [ timestamp ]

Creates Kodi-compatible .nfo files for a folder full of TV shows

Folder is named: "TV Show Name (Year)"
<br/>Will default to current directory unless directory provided as argument

TV episodes are inside this folder, named: "SSxEE anything.ext"
<br/>where SS is season number - can be 1,2,3,4 digits
<br/>NN is episode number - can be 1,2,3 digits
<br/>Leading zeroes are allowed but optional.
<br/>anything can be name of episode or name of series
<br/>.ext is .mp4 .mkv or .avi ; e.g:
<br/>01x01 An Unearthly Child.mkv

Need to convert sXXeXX filenames to SSxEE ? Try rename command:
<br/>`rename -v ("s/^(.*)s(\d+)e(\d+)(.*)$/\$1x\$2 \$3 \$4/i") * -n`
<br/>(-n does dry run; remove -n to make changes permanent)

timestamp is optional, it is the time from which a thumbnail is taken
<br/>hh:mm:ss where hh=hour, mm=minutues, ss=second
<br/>You can give decimal seconds, e.g. 00:02:30.15
for two minutes, thirty seconds and fifteen hundredths of a second
<br/>if not supplied it defaults to 2 minutes 00:02:00
or you can provide -n --nothumbnail

For artwork for whole series, inside folder have literally named files:
<br/>fanart.jpg 1920x1080
<br/>poster.jpg 1000x1500

Options:
<br/>-h --help       This help text
<br/>-n --nothumnail Do not create episode thumbnails
<br/>-q --quiet      Do not produce progress information
<br/>-f --force      Overwrite existing .nfo and thumnail files
<br/>                (default is not to overwrite)
