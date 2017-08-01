
We've created a number of [tutorials](http://data.syrgov.net/pages/tutorial) to help you use Python with DataCuse open data. Here, we will walk you through how to create a map of the sidewalk cafes in Syracuse using ESRI's Python developer toolkit. The benefit of this library is that your maps are connected to the live dataset, so if there is a change to the data, your map will change too.

Import modules


```python
from arcgis.gis import *
from IPython.display import display
gis = GIS()
```

Now you will create the basemap you will use. You need to search for the city (in this case Syracuse) and how zoomed in the map should be. The syntax is as follows:
[map name] = gis.map('[insert location here]', [insert zoom here])


```python
syracuse_map = gis.map('Syracuse, NY', 13)
```

Display the map. At first you'll just see a blank map. The following steps will add the points to the map.


```python
display(syracuse_map)
```



You will need to find the dataset that you want to add. In this case, the dataset you are looking for is called "City of Syracuse Sidewalk Cafes". When you use the gis.content.search function, you can search for any dataset. You can also filter by item type - these can include feature layers, CSVs, and more. In this case we will use a feature layer as it is ready to easily be placed on a map. 

When you search, there may be multiple results that are returned. In this case, since the dataset is specifically named, there is only one result. What you see below is as follows:

First we search for the correct dataset using: search_subset = gis.content.search("City of Syracuse Sidewalk Cafes", item_type = 'Feature Layer') We assign the results of the search to search_subset.

Then, since there is only one result, we assign that dataset to subset_item like this: subset_item = search_subset[0]. You'll notice the [0]. This means that we are selecting the first result from search_subset. In Python, the first result is 0, second result is 1, and so on.


```python
search_subset = gis.content.search("City of Syracuse Sidewalk Cafes", item_type = 'Feature Layer')
subset_item = search_subset[0]
subset_item
```




<div class="item_container" style="height: auto; overflow: hidden; border: 1px solid #cfcfcf; border-radius: 2px; background: #f6fafa; line-height: 1.21429em; padding: 10px;">
                    <div class="item_left" style="width: 210px; float: left;">
                       <a href='http://www.arcgis.com/home/item.html?id=1d53f4e926034301a18d4c81d95c6d86' target='_blank'>
                        <img src='http://www.arcgis.com/sharing/rest//content/items/1d53f4e926034301a18d4c81d95c6d86/info/thumbnail/ago_downloaded.png' class="itemThumbnail">
                       </a>
                    </div>

                    <div class="item_right"     style="float: none; width: auto; overflow: hidden;">
                        <a href='http://www.arcgis.com/home/item.html?id=1d53f4e926034301a18d4c81d95c6d86' target='_blank'><b>City of Syracuse Sidewalk Cafes</b>
                        </a>
                        <br/><img src='http://www.arcgis.com/home/js/jsapi/esri/css/images/item_type_icons/featureshosted16.png' style="vertical-align:middle;">Feature Layer Collection by samedelstein
                        <br/>Last Modified: August 01, 2017
                        <br/>0 comments, 12 views
                    </div>
                </div>
                



Now we add the points to the map. We take the original map (syracuse_map) and tell it to add the subset_item (our sidewalk cafes) to the map. When you run this line of code, you'll see the points on the map above.


```python
syracuse_map.add_layer(subset_item)
```

To add one more step to the process, maybe you want the background of the map to look different. The background of the map is called a basemap, and there are many different options. You can search for the different options and decide which one you like best.


```python
basemaps = gis.content.search("tags:esri_basemap AND owner:esri", item_type = "web map")
for basemap in basemaps:
    display(basemap)
```


<div class="item_container" style="height: auto; overflow: hidden; border: 1px solid #cfcfcf; border-radius: 2px; background: #f6fafa; line-height: 1.21429em; padding: 10px;">
                    <div class="item_left" style="width: 210px; float: left;">
                       <a href='http://www.arcgis.com/home/item.html?id=8bf7167d20924cbf8e25e7b11c7c502c' target='_blank'>
                        <img src='http://www.arcgis.com/sharing/rest//content/items/8bf7167d20924cbf8e25e7b11c7c502c/info/thumbnail/world_street_map.jpg' class="itemThumbnail">
                       </a>
                    </div>

                    <div class="item_right"     style="float: none; width: auto; overflow: hidden;">
                        <a href='http://www.arcgis.com/home/item.html?id=8bf7167d20924cbf8e25e7b11c7c502c' target='_blank'><b>Streets</b>
                        </a>
                        <br/>Presents highway-level data for the world and street-level data for North America, Europe and more.<img src='http://www.arcgis.com/home/js/jsapi/esri/css/images/item_type_icons/maps16.png' style="vertical-align:middle;">Web Map by esri
                        <br/>Last Modified: December 08, 2016
                        <br/>0 comments, 2,778,323 views
                    </div>
                </div>
                



<div class="item_container" style="height: auto; overflow: hidden; border: 1px solid #cfcfcf; border-radius: 2px; background: #f6fafa; line-height: 1.21429em; padding: 10px;">
                    <div class="item_left" style="width: 210px; float: left;">
                       <a href='http://www.arcgis.com/home/item.html?id=d5e02a0c1f2b4ec399823fdd3c2fdebd' target='_blank'>
                        <img src='http://www.arcgis.com/sharing/rest//content/items/d5e02a0c1f2b4ec399823fdd3c2fdebd/info/thumbnail/topo_map_2.jpg' class="itemThumbnail">
                       </a>
                    </div>

                    <div class="item_right"     style="float: none; width: auto; overflow: hidden;">
                        <a href='http://www.arcgis.com/home/item.html?id=d5e02a0c1f2b4ec399823fdd3c2fdebd' target='_blank'><b>Topographic</b>
                        </a>
                        <br/>Topographic map which includes boundaries, cities, water features, physiographic features, parks, landmarks, transportation, and buildings.<img src='http://www.arcgis.com/home/js/jsapi/esri/css/images/item_type_icons/maps16.png' style="vertical-align:middle;">Web Map by esri
                        <br/>Last Modified: June 19, 2017
                        <br/>3 comments, 1,482,439 views
                    </div>
                </div>
                



<div class="item_container" style="height: auto; overflow: hidden; border: 1px solid #cfcfcf; border-radius: 2px; background: #f6fafa; line-height: 1.21429em; padding: 10px;">
                    <div class="item_left" style="width: 210px; float: left;">
                       <a href='http://www.arcgis.com/home/item.html?id=716b600dbbac433faa4bec9220c76b3a' target='_blank'>
                        <img src='http://www.arcgis.com/sharing/rest//content/items/716b600dbbac433faa4bec9220c76b3a/info/thumbnail/Imagery_Labels.jpg' class="itemThumbnail">
                       </a>
                    </div>

                    <div class="item_right"     style="float: none; width: auto; overflow: hidden;">
                        <a href='http://www.arcgis.com/home/item.html?id=716b600dbbac433faa4bec9220c76b3a' target='_blank'><b>Imagery with Labels</b>
                        </a>
                        <br/>Satellite and high-resolution aerial imagery for the world with political boundaries and place names. You can turn on transportation including street names.<img src='http://www.arcgis.com/home/js/jsapi/esri/css/images/item_type_icons/maps16.png' style="vertical-align:middle;">Web Map by esri
                        <br/>Last Modified: December 08, 2016
                        <br/>3 comments, 1,416,276 views
                    </div>
                </div>
                



<div class="item_container" style="height: auto; overflow: hidden; border: 1px solid #cfcfcf; border-radius: 2px; background: #f6fafa; line-height: 1.21429em; padding: 10px;">
                    <div class="item_left" style="width: 210px; float: left;">
                       <a href='http://www.arcgis.com/home/item.html?id=fe44cf9a739848939988addfeba473e4' target='_blank'>
                        <img src='http://www.arcgis.com/sharing/rest//content/items/fe44cf9a739848939988addfeba473e4/info/thumbnail/Terrain_Labels.jpg' class="itemThumbnail">
                       </a>
                    </div>

                    <div class="item_right"     style="float: none; width: auto; overflow: hidden;">
                        <a href='http://www.arcgis.com/home/item.html?id=fe44cf9a739848939988addfeba473e4' target='_blank'><b>Terrain with Labels</b>
                        </a>
                        <br/>Basemap features shaded relief, bathymetry and coastal water features that provide neutral background with political boundaries and placenames.<img src='http://www.arcgis.com/home/js/jsapi/esri/css/images/item_type_icons/maps16.png' style="vertical-align:middle;">Web Map by esri
                        <br/>Last Modified: December 08, 2016
                        <br/>0 comments, 1,175,871 views
                    </div>
                </div>
                



<div class="item_container" style="height: auto; overflow: hidden; border: 1px solid #cfcfcf; border-radius: 2px; background: #f6fafa; line-height: 1.21429em; padding: 10px;">
                    <div class="item_left" style="width: 210px; float: left;">
                       <a href='http://www.arcgis.com/home/item.html?id=55ebf90799fa4a3fa57562700a68c405' target='_blank'>
                        <img src='http://www.arcgis.com/sharing/rest//content/items/55ebf90799fa4a3fa57562700a68c405/info/thumbnail/streets_map.jpg' class="itemThumbnail">
                       </a>
                    </div>

                    <div class="item_right"     style="float: none; width: auto; overflow: hidden;">
                        <a href='http://www.arcgis.com/home/item.html?id=55ebf90799fa4a3fa57562700a68c405' target='_blank'><b>Streets</b>
                        </a>
                        <br/>This web map provides a detailed vector basemap for the world with a classic Esri street map style. <img src='http://www.arcgis.com/home/js/jsapi/esri/css/images/item_type_icons/maps16.png' style="vertical-align:middle;">Web Map by esri
                        <br/>Last Modified: June 28, 2017
                        <br/>2 comments, 1,140,741 views
                    </div>
                </div>
                



<div class="item_container" style="height: auto; overflow: hidden; border: 1px solid #cfcfcf; border-radius: 2px; background: #f6fafa; line-height: 1.21429em; padding: 10px;">
                    <div class="item_left" style="width: 210px; float: left;">
                       <a href='http://www.arcgis.com/home/item.html?id=979c6cc89af9449cbeb5342a439c6a76' target='_blank'>
                        <img src='http://www.arcgis.com/sharing/rest//content/items/979c6cc89af9449cbeb5342a439c6a76/info/thumbnail/light_canvas_map.jpg' class="itemThumbnail">
                       </a>
                    </div>

                    <div class="item_right"     style="float: none; width: auto; overflow: hidden;">
                        <a href='http://www.arcgis.com/home/item.html?id=979c6cc89af9449cbeb5342a439c6a76' target='_blank'><b>Light Gray Canvas</b>
                        </a>
                        <br/>This web map provides a detailed vector basemap for the world featuring a neutral background style with minimal colors, labels, and features. <img src='http://www.arcgis.com/home/js/jsapi/esri/css/images/item_type_icons/maps16.png' style="vertical-align:middle;">Web Map by esri
                        <br/>Last Modified: June 28, 2017
                        <br/>0 comments, 1,135,089 views
                    </div>
                </div>
                



<div class="item_container" style="height: auto; overflow: hidden; border: 1px solid #cfcfcf; border-radius: 2px; background: #f6fafa; line-height: 1.21429em; padding: 10px;">
                    <div class="item_left" style="width: 210px; float: left;">
                       <a href='http://www.arcgis.com/home/item.html?id=358ec1e175ea41c3bf5c68f0da11ae2b' target='_blank'>
                        <img src='http://www.arcgis.com/sharing/rest//content/items/358ec1e175ea41c3bf5c68f0da11ae2b/info/thumbnail/dark_canvas_map.jpg' class="itemThumbnail">
                       </a>
                    </div>

                    <div class="item_right"     style="float: none; width: auto; overflow: hidden;">
                        <a href='http://www.arcgis.com/home/item.html?id=358ec1e175ea41c3bf5c68f0da11ae2b' target='_blank'><b>Dark Gray Canvas</b>
                        </a>
                        <br/>This web map provides a detailed vector basemap for the world featuring a neutral background style with minimal colors, labels, and features. <img src='http://www.arcgis.com/home/js/jsapi/esri/css/images/item_type_icons/maps16.png' style="vertical-align:middle;">Web Map by esri
                        <br/>Last Modified: June 28, 2017
                        <br/>0 comments, 1,130,667 views
                    </div>
                </div>
                



<div class="item_container" style="height: auto; overflow: hidden; border: 1px solid #cfcfcf; border-radius: 2px; background: #f6fafa; line-height: 1.21429em; padding: 10px;">
                    <div class="item_left" style="width: 210px; float: left;">
                       <a href='http://www.arcgis.com/home/item.html?id=86265e5a4bbb4187a59719cf134e0018' target='_blank'>
                        <img src='http://www.arcgis.com/sharing/rest//content/items/86265e5a4bbb4187a59719cf134e0018/info/thumbnail/imagery_hybrid2.jpg' class="itemThumbnail">
                       </a>
                    </div>

                    <div class="item_right"     style="float: none; width: auto; overflow: hidden;">
                        <a href='http://www.arcgis.com/home/item.html?id=86265e5a4bbb4187a59719cf134e0018' target='_blank'><b>Imagery Hybrid</b>
                        </a>
                        <br/>Satellite and high-resolution aerial imagery for the world with political boundaries, roads, and labels for places and roads.<img src='http://www.arcgis.com/home/js/jsapi/esri/css/images/item_type_icons/maps16.png' style="vertical-align:middle;">Web Map by esri
                        <br/>Last Modified: February 14, 2017
                        <br/>0 comments, 1,023,269 views
                    </div>
                </div>
                



<div class="item_container" style="height: auto; overflow: hidden; border: 1px solid #cfcfcf; border-radius: 2px; background: #f6fafa; line-height: 1.21429em; padding: 10px;">
                    <div class="item_left" style="width: 210px; float: left;">
                       <a href='http://www.arcgis.com/home/item.html?id=8b3d38c0819547faa83f7b7aca80bd76' target='_blank'>
                        <img src='http://www.arcgis.com/sharing/rest//content/items/8b3d38c0819547faa83f7b7aca80bd76/info/thumbnail/light_canvas.jpg' class="itemThumbnail">
                       </a>
                    </div>

                    <div class="item_right"     style="float: none; width: auto; overflow: hidden;">
                        <a href='http://www.arcgis.com/home/item.html?id=8b3d38c0819547faa83f7b7aca80bd76' target='_blank'><b>Light Gray Canvas</b>
                        </a>
                        <br/>This web map draws attention to your thematic content by providing a neutral background with minimal colors, labels, and features.<img src='http://www.arcgis.com/home/js/jsapi/esri/css/images/item_type_icons/maps16.png' style="vertical-align:middle;">Web Map by esri
                        <br/>Last Modified: December 08, 2016
                        <br/>44 comments, 471,140 views
                    </div>
                </div>
                



<div class="item_container" style="height: auto; overflow: hidden; border: 1px solid #cfcfcf; border-radius: 2px; background: #f6fafa; line-height: 1.21429em; padding: 10px;">
                    <div class="item_left" style="width: 210px; float: left;">
                       <a href='http://www.arcgis.com/home/item.html?id=d94dcdbe78e141c2b2d3a91d5ca8b9c9' target='_blank'>
                        <img src='http://www.arcgis.com/sharing/rest//content/items/d94dcdbe78e141c2b2d3a91d5ca8b9c9/info/thumbnail/natgeo.jpg' class="itemThumbnail">
                       </a>
                    </div>

                    <div class="item_right"     style="float: none; width: auto; overflow: hidden;">
                        <a href='http://www.arcgis.com/home/item.html?id=d94dcdbe78e141c2b2d3a91d5ca8b9c9' target='_blank'><b>National Geographic Map</b>
                        </a>
                        <br/>This map is designed to be used as a general reference map for informational and educational purposes as well as a basemap by GIS professionals and other users for creating web maps and web mapping applications.<img src='http://www.arcgis.com/home/js/jsapi/esri/css/images/item_type_icons/maps16.png' style="vertical-align:middle;">Web Map by esri
                        <br/>Last Modified: December 08, 2016
                        <br/>4 comments, 412,226 views
                    </div>
                </div>
                


The basemap options have names that you use in the python code. Those are as follows:


```python
syracuse_map.basemaps
```




    ['streets',
     'satellite',
     'hybrid',
     'topo',
     'gray',
     'dark-gray',
     'oceans',
     'national-geographic',
     'terrain',
     'osm']



When you have selected the basemap you like, simply assign it to the map you created before using [map name].basemap = '[chosen basemap]'


```python
syracuse_map.basemap = 'gray'
```


```python
display(syracuse_map)
```



You're all done! You'll see that you now have a map with points. You can click on each of those points to see details. Now you can choose where to go and enjoy some lunch or dinner outside!
