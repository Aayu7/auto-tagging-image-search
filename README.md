# Search Images By Tagging Them
Tagging photos provides much better search capabilities, in this project I'm trying to build an inteligient way to search for images using image recongnition (google-vision).

This project can be used as a backend for backup solution, users only have to upload thier images and its automatically gets tagged by google-vision services. 

Also, it provides a translation capability,for example if translation for arabic is enabled. Once the image got tags (lables) from google-vision service, all these tags will be translated using google-translation-api. So the user searches for 'مركبة' ( veichele in arabic) or searches for viechele will get the same result.

All these processes are done async, as showin in HOW IT WORKs section, once the recognition and the translation process are done, a document for this image will be stored in ElasticSearch like the following : 

```
{
	"uploaded_at": "2017-03-25 08:54:15",
	"image_path": "/opt/personal/search-images-tags/datadir/flowers.jpg",
	"image_type": ".jpg",
	"timestamp": 1490428776,
	"en_lables": [
		"flower",
		"flora",
		"plant",
		"flower bouquet",
		"flower arranging",
		"floristry",
		"land plant",
		"petal",
		"macro photography",
		"flowering plant"
	],
	"image_fname": "flowers.jpg",
	"ar_lables": [
		"زهرة",
		"النباتية",
		"نبات",
		"باقة من الزهور",
		"ترتيب الزهور",
		"التزيين بالزهور",
		"نبات الأرض",
		"البتلة نبات",
		"تصوير الماكرو",
		"النباتات المزهرة"
	]
}
```
## HOW IT WORKS

![Alt text](/examples/tagging-images.png?raw=true "Optional Title")

## HOW TO RUN IT
1) Edit the config.ini file
2) Run the HTTP interface
```
$ python main.py
```
3) Run the Consumer Process
```
$ python consumer.py
```

