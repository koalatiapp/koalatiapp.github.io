# Koalati marketing website

This a static HTML website extracted from a Webflow design and hosted with 
Github Pages.


## Updating the site

If the Webflow site is updated, you can fetch an updated version of it with the
script below, and simply replace the current files in this repo with the new 
ones.

Note: this script is built for MacOS.  
It may very well not work on other OSes.

```bash
#!/bin/bash
# Exports the https://koalati.webflow.io website to a static HTML site

# Download the entire site
wget --mirror --no-clobber --page-requisites --html-extension --convert-links --page-requisites --span-hosts --restrict-file-names=windows --domains=webflow.io,uploads-ssl.webflow.com --no-parent -e robots=off --compression=none https://koalati.webflow.io

# Uncompress assets like CSS & JS
find . \( -type d -name .git -prune \) -o -type f -name "*.html"  -print0 | xargs -0 sed -i '' -e 's/\.css\.gz/.css/g'
find . \( -type d -name .git -prune \) -o -type f -name "*.html"  -print0 | xargs -0 sed -i '' -e 's/\.js\.gz/.js/g'
find . \( -type d -name .git -prune \) -o -type f -name "*.gz" -print0 | xargs -0 gzip -d

# Move asset subdirectories to the main directory
mkdir koalati.webflow.io/assets
mv uploads-ssl.webflow.com/* koalati.webflow.io/assets
rm -rf uploads-ssl.webflow.com
find . \( -type d -name .git -prune \) -o -type f -name "*.html"  -print0 | xargs -0 sed -i '' -e 's/\.\.\/\(\.\.\/\)*uploads-ssl\.webflow\.com/\1assets/g'

# Fix video embeds
find . \( -type d -name .git -prune \) -o -type f -name "*.html"  -print0 | xargs -0 sed -i '' -e 's/"https:\/\/koalati\.webflow\.io\/.*\\&quot;\/\//\\"https:\/\//g'
find . \( -type d -name .git -prune \) -o -type f -name "*.html"  -print0 | xargs -0 sed -i '' -e 's/\\&quot;"/\\"/g'
find . \( -type d -name .git -prune \) -o -type f -name "*.html"  -print0 | xargs -0 sed -i '' -e 's/&amp;/\&/g'
find . \( -type d -name .git -prune \) -o -type f -name "*.html"  -print0 | xargs -0 sed -i '' -e 's/"https:\/\/cdn\.embedly\.com\/widgets\/media?src=\([^&]*\).*\\"/"\1\\"/g'
# URL decoding: `:`
find . \( -type d -name .git -prune \) -o -type f -name "*.html"  -print0 | xargs -0 sed -i '' -e 's/\(embedly-embed\\" src=\\"[^\\]*\)%3A/\1:/g'
# URL decoding: `?`
find . \( -type d -name .git -prune \) -o -type f -name "*.html"  -print0 | xargs -0 sed -i '' -e 's/\(embedly-embed\\" src=\\"[^\\]*\)%3F/\1?/g'
# URL decoding: reoccurring characters (do it a few times to get them all - not optimal but it works)
for i in {1..10}
do
	# URL decoding: `/`
	find . \( -type d -name .git -prune \) -o -type f -name "*.html"  -print0 | xargs -0 sed -i '' -e 's/\(embedly-embed\\" src=\\"[^\\]*\)%2F/\1\//g'
	# URL decoding: `=`
	find . \( -type d -name .git -prune \) -o -type f -name "*.html"  -print0 | xargs -0 sed -i '' -e 's/\(embedly-embed\\" src=\\"[^\\]*\)%3D/\1=/g'
	# URL decoding: `&`
	find . \( -type d -name .git -prune \) -o -type f -name "*.html"  -print0 | xargs -0 sed -i '' -e 's/\(embedly-embed\\" src=\\"[^\\]*\)%26/\1\&/g'
done

# Remove .html extension in URLs
find . \( -type d -name .git -prune \) -o -type f -name "*.html"  -print0 | xargs -0 sed -i '' -e 's/\.html//g'

# Clean up empty # links
find . \( -type d -name .git -prune \) -o -type f -name "*.html"  -print0 | xargs -0 sed -i '' -e 's/href="[^"]*#"/href="#"/g'

# Change /index link to just /
find . \( -type d -name .git -prune \) -o -type f -name "*.html"  -print0 | xargs -0 sed -i '' -e 's/href="\(\.\.\/\)*index"/href="\/"/g'
find . \( -type d -name .git -prune \) -o -type f -name "*.html"  -print0 | xargs -0 sed -i '' -e 's/href="[^"]*#content-start"/href="#content-start"/g'

echo "Site downloaded!"
echo "Replace the files in the git repository with these new ones and git push to update the site!"
```
