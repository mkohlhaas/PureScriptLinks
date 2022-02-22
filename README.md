1. Check number of pages:
```shell
curl -I -H "Accept: application/vnd.github.v3+json" "https://GITHUB_TOKEN:x-oauth-basic@api.github.com/search/repositories?q=PureScript"
```
2. Download all links
```shell
for i in {1..34}; do curl -H "Accept: application/vnd.github.v3+json" "https://GITHUB_TOKEN:x-oauth-basic@api.github.com/search/repositories?q=PureScript&page=$i" >> pslinks.txt; done
```
3. Clean up pslinks.txt.
4. Download packages:
```shell
while read line; do $line; done < pslinks.txt
```
or simply:
```shell
source ./pslinks.txt
```
5. Unpack zip files:
```shell
for i in *.zip; do ark --batch $i; done
```
