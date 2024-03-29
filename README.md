# useful-one-liners

Terminal commands/pipes/mini-scripts I always have to search for :/

## Apache stop all

Need to do this before starting Local WP on some machines.

`sudo apachectl stop`

## Audible to mp3

`ffmpeg -activation_bytes 036b933a -i INPUT OUTPUT.mp3`

batch:

`for i in *.aax; do ffmpeg -activation_bytes 036b933a -i  "$i" "${i%.*}.mp3"; done`

[Get Activation Bytes](https://audible-converter.ml)

## Broken Packages Fix

When Ubuntu surprises me with `E: Unable to correct problems, you have held broken packages`, doing whatever you were trying to do with `aptitude` is *usually* the solution.

## Compress images

`jpegoptim -v --size=240k file_name.jpg`

## Crop the surrounding transparent part / whitespace from images

requires imagemagick

`convert input.png -trim +repage output.png`

## Force new IP address

`sudo dhclient -r && sudo dhclient`

## Github clone all my repositories

`gh repo list koljapluemer --limit 1000 | awk '{print $1; }' | xargs -L1 gh repo clone`

Assumes `gh` is installed.

- *TODO*: allow to exclude repos starting with `_`, or archived repos (which should be the same)

## Git push to all remotes

`git remote | xargs -L1 git push --all`

## Heroku CLI add repository to existing app

`heroku git:remote -a example-app`

<https://devcenter.heroku.com/articles/git#for-an-existing-app>

## Kill all instances of a given software

`killall -s SIGKILL firefox`

## Merge PDFs

`pdfunite file_start_or_whatever* out.pdf`

## Share localhost

now that ngrok is paid and commercial and annoying:

`npx localtunnel --port 8000`

(it's an npm package)

## Refresh stale python repos

*(maybe learn to handle `poetry` instead)*

On encountering some ancient Python project with a `requirements.txt` containing old, hard-coded versions of libraries, do the following:

* copy-paste the `requirements.txt`
* if needed: `pip install pip-tools`
* `pip-compile -U requirements.txt`

## webp to jpg batch convert

the web meme convertor

```
for i in *.webp; do name=`echo "$i" | cut -d'.' -f1`; echo "$name"; convert "$i" "${name}.jpg"; done
```

## youtube-dl audio only

getting podcasts on my mp3 player like:

`yt-dlp -f 'bestaudio[ext=m4a]' "http://youtu.be/XXXXXXXXX"`
