# ffmerge
Bash script to use ffmpeg to merge all videos in a directory (without re-encoding, or converting to a different format)

## Dependancies
ffmpeg: https://www.ffmpeg.org/

## Installation
Simply access the file ffmerge using terminal. If you are unable to execute the script, run the following command:

`chmod u+x`

<br>

# Usage
Syntax: <br>
`ffmerge targetdirectory fileextension outputfile`
<br> Example: <br>
`./ffmerge /Users/nkmultimdia/Movies .mov mergedOutput.mov`<br>
The above command will merge all .mov files in the folder /Users/nkmultimedia/Movies to create the file mergedOutput.mov

<br>

# Notes
* ffmerge also supports merging audio files
* It is assumed that all target files have originated from the **same device** (encoded using the same codec, container, dimensions, etc)
* Files created from different sources (different devices) cannot be merged. If you're trying to merge videos shot on a cellphone, all videos should have been captured on the same device (see **ffmpeg concat** command and **-c** flag for further info)

<br><br>
# How it works
* ffmpeg concat function lets users merge files by reading a text file (containing the list of files to be merged)
* ffmerge navigates to the target director, and generates a text file **concat.txt**, and popuplates it with all files of the given extension (ex: \*.mp4) found in the directory
* concat.txt is used as an input to ffmpeg to merge the videos
* The target codec is set to copy the streams present in the source videos. This prevents re-encoding of the videos.
