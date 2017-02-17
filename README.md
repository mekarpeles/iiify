# niiifty

A simple Python Flask-based implementation of the IIIF Image API

## Notes
* This started as a toy project to learn the IIIF API, so it is not necessarily ready for production, but may be some day.
* It was also an opportunity to learn Flask, a micro-framework. I consciously chose to avoid adding too many abstractions, and attempted to stick to procedural code as much as possible.
* It has a simple on-disk cache scheme, but no cache management.
  * If you want to delete the cache, purge the contents of the cache directory.
  * Cache does not currently check timestamps.
  * Cache can't be disabled yet.
* It was a lot of fun, and does work, but is missing a lot of optimizations.
* There are several sample files in the media directory - all but one are courtesy of the Getty's Open Content Program.

## Installation & Setup

1. Clone this repo
2. Setup a virtualenv (optional)
3. do `pip install -r requirements.txt`
4. do `python app.py`
5. You now have a simple IIIF server running at http://127.0.0.1:8080

## Configuration

Want to *enable CORS*?

Touch/create the file `settings.cfg` within the `configs/` directory with the following contents:

    [server]
    cors = 1

For a list of other configurable options, see file `configs/__init__.py` which is responsible for parsing the configuration options specified in settings.cfg or setting sane defaults in the absence of a specified option.

## Quick Start

List all known identifiers
* http://127.0.0.1:8080

Retrieve large.jpg as 800px wide JPEG
* http://127.0.0.1:8080/large.jpg/full/800,/0/default.jpg 

Crop into large.jpg and return 800px wide JPEG
* http://127.0.0.1:8080/large.jpg/full/800,/0/default.jpg 

Mirror large.jpg horizontally and return 800px wide JPEG
* http://127.0.0.1:8080/large.jpg/full/800,/!0/default.jpg 

For more information, read the specification at http://iiif.io/technical-details.html
