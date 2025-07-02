---
layout: single
title: "Abundance NY City Council Endorsements"
date: 2025-06-30
categories: [maps]
tags: [python, geopandas, datawrapper]
author_profile: true
classes: wide
# toc: true
# toc_label: "Contents"
# toc_sticky: true
---
<style>
.page__content {
  font-size: 0.9rem;
}

.code-container {
  max-width: 600px;
  margin: 20px 0;
  border: 1px solid #ddd;
  border-radius: 4px;
  background: #f8f9fa;
}

.code-header {
  background: #e9ecef;
  padding: 8px 12px;
  border-bottom: 1px solid #ddd;
  font-size: 14px;
  font-weight: bold;
}

.code-content {
  padding: 12px;
  font-family: 'Courier New', monospace;
  font-size: 12px;
  line-height: 1.4;
  overflow-x: auto;
  max-height: 300px;
  overflow-y: auto;
}

/* Spreadsheet table styling */
.spreadsheet-table {
  border-collapse: collapse;
  font-family: Arial, sans-serif;
  font-size: 13px;
  margin: 20px 0;
  width: 100%;
  overflow-x: auto;
  display: block;
  white-space: nowrap;
}

.spreadsheet-table thead {
  display: table-header-group;
}

.spreadsheet-table tbody {
  display: table-row-group;
}

.spreadsheet-table tr {
  display: table-row;
}

.spreadsheet-table th,
.spreadsheet-table td {
  display: table-cell;
  border: 1px solid #d0d7de;
  padding: 6px 8px;
  text-align: left;
  vertical-align: top;
  max-width: 200px;
  overflow: hidden;
  text-overflow: ellipsis;
}

.spreadsheet-table th {
  background-color: #f6f8fa;
  font-weight: 600;
  color: #24292f;
  position: sticky;
  top: 0;
}

.spreadsheet-table td {
  background-color: #ffffff;
}

.spreadsheet-table tr:nth-child(even) td {
  background-color: #f6f8fa;
}

.spreadsheet-table tr:hover td {
  background-color: #fff8dc;
}

/* Column specific widths */
.col-district { width: 60px; }
.col-endorsed { width: 80px; }
.col-name { width: 120px; }
.col-incumbency { width: 90px; }
.col-tagline { width: 180px; }
.col-photo { width: 80px; }
.col-campaign { width: 100px; }
.col-neighborhoods { width: 250px; }
.col-tooltip { width: 300px; }
.col-also { width: 120px; }
.col-dont { width: 100px; }
</style>


<!-- 1) DATAWRAPPER MAP – Plot | Text -->
<div style="display: grid; grid-template-columns: 50% 50%; gap: 1.5rem; margin-bottom: 2rem;">
  <!-- Left: Datawrapper -->
  <div style="position:relative; max-width:100%; overflow: hidden; box-shadow: 0 6px 20px rgba(0,0,0,0.25); max-height: 780px;">
    <iframe
      title="Abundance NY City Council Endorsements Map"
      aria-label="Map"
      id="datawrapper-chart-0xyMH"
      src="https://datawrapper.dwcdn.net/0xyMH/7/"
      scrolling="no"
      frameborder="0"
      style="width: 100%; max-width: 100%; border: none;"
      height="780"
      data-external="1">
    </iframe>
    <script type="text/javascript">
      !function(){"use strict";window.addEventListener("message",(function(e){
        if(void 0!==e.data["datawrapper-height"]){
          var iframes=document.querySelectorAll("iframe");
          for(var key in e.data["datawrapper-height"]){
            for(var i=0;i<iframes.length;i++){
              if(iframes[i].contentWindow===e.source){
                iframes[i].style.height=e.data["datawrapper-height"][key]+"px";
              }
            }
          }
        }
      }))}();
    </script>
  </div>
  <!-- Right: caption -->
  <div>
    <p style="margin-top: 2rem;"> I made this map for Abundance NY ahead of the NYC primaries to share a fun infograph of councilor endorsements, especially for down-ballot races where people may not know the candidates as well. This was mostly an excuse to use Datawrapper, since it is so universally beloved (for good reason!). Also, I'm fully on-board with the Abundance agenda, and have been attending a lot of Abundance NY meetups since returning to NYC.</p> 
    
    <p>This was a quick map to build, but I did have to simplify geometries with GeoPandas and convert the shapefile for use in Datawrapper. It also got a lot of views!</p>
    <div style="border-left: 4px solid #007acc; background-color: #f0f8ff; padding: 1em; margin-top: 2rem;">

  <p><strong>Datawrapper has some prerequisites if you're using your own maps.</strong></p>
  <p><u>Prerequisites</u><br>
  To upload your map in Datawrapper, it needs to...<br>
  – be in the TopoJSON or GeoJSON format<br>
  – be smaller than 2MB<br>
  – use the WGS-84 coordinate system (EPSG:4326 projection)</p>
</div>

</div>




</div>
<div>
  <p>So the first step is to go to NYC City Planning to get the council district shapes:<br>
  <a href="https://www.nyc.gov/content/planning/pages/resources/datasets/city-council" target="_blank" rel="noopener">
    NYC Planning
  </a>.
  You can either download them as shapefiles, or just copy the url for "View GeoJSON" if you want to work with GeoJSON off the jump (I'll go through both ways).</p>

  <p>Below, I'll walk through all the steps, but if you want to open the walk-through in a MyBinder session and play with the code, you can do that here (takes a minute to load):</p>

  <p>
    <a href="https://mybinder.org/v2/gh/samforwill/nycc-map/HEAD?urlpath=/doc/tree/nycc_districts.ipynb" target="_blank" rel="noopener"
       style="background-color: #007acc; color: white; padding: 0.5em 1em; border-radius: 4px; text-decoration: none;">
      Launch MyBinder Notebook →
    </a>
  </p>
</div>
<!-- {: .small} -->
### NYC City Council Districts - GeoPandas Simplification Walkthrough

##### Setup

First, import GeoPandas, pandas, and os.  
I'll load the City Council boundaries into a GeoDataFrame directly from the GeoJSON endpoint we got from NYC Planning (url) just to show how to do that. Then I'll follow up in the next cell with loading them as shapefiles. I'll also verify the coordinate reference system (CRS), since Datawrapper requires EPSG 4326 (WGS 84).

```python
import geopandas as gpd
import pandas as pd
import os

url = "https://services5.arcgis.com/GfwWNkhOj9bNBqoJ/arcgis/rest/services/NYC_City_Council_Districts/FeatureServer/0/query?where=1=1&outFields=*&outSR=4326&f=pgeojson"
nycc_gdf = gpd.read_file(url)
nycc_gdf.crs
```

> <Geographic 2D CRS: EPSG:4326>  
> Name: WGS 84  
> Axis Info [ellipsoidal]:  
> - Lat[north]: Geodetic latitude (degree)  
> - Lon[east]: Geodetic longitude (degree)  
> Area of Use:  
> - name: World.  
> - bounds: (-180.0, -90.0, 180.0, 90.0)  
> Coordinate Operation:  
> - name: unknown  
> - method: unknown  
> Datum: World Geodetic System 1984 ensemble  
> - Ellipsoid: WGS 84  
> - Prime Meridian: Greenwich

Great! So that's already projected in EPSG:4326. I already know it's 5.5MB, so we'd still have to do simplification to meet Datawrapper's file size limit, but I'll show how with the shapefile below.

```python
nycc_gdf = gpd.read_file("data/nycc_25b/nycc.shp")
nycc_gdf.crs
```

> <Projected CRS: EPSG:2263>  
> Name: NAD83 / New York Long Island (ftUS)  
> Axis Info [cartesian]:  
> - X[east]: Easting (US survey foot)  
> - Y[north]: Northing (US survey foot)  
> Area of Use:  
> - name: United States (USA) - New York - counties of Bronx; Kings; Nassau; New York; Queens; Richmond; Suffolk.  
> - bounds: (-74.26, 40.47, -71.51, 41.3)  
> Coordinate Operation:  
> - name: SPCS83 New York Long Island zone (US Survey feet)  
> - method: Lambert Conic Conformal (2SP)  
> Datum: North American Datum 1983  
> - Ellipsoid: GRS 1980  
> - Prime Meridian: Greenwich

But it's in EPSG:2263, so let's reproject it into 4326, and define a little function to save it as a file and also print the file size when we are tinkering with simplification later.

```python
def save_geojson_print_size(gdf, output_path):
    gdf.to_file(output_path, driver="GeoJSON")
    size_mb = os.path.getsize(output_path)/(1024 *1024)
    print(f"{output_path} is {size_mb:.2f} MB")

output_path = "data/nycc.geojson"
nycc_gdf = nycc_gdf.to_crs("EPSG:4326")
save_geojson_print_size(nycc_gdf, output_path)
```

> data/nycc.geojson is 5.54 MB


#### Simplifying Geometries

So we have to simplify the geometries by more than half. That actually takes a bit of tinkering around. Defining a new gdf on the copy of the original prevents making our iterations lossy (simplifying a geometry that's already been simplified). We use `preserve_topology=True` to prevent self-intersecting and invalid geometries.

```python
simplified_gdf = nycc_gdf.copy()
simplified_gdf["geometry"] = nycc_gdf["geometry"].simplify(tolerance=10, preserve_topology=True)  # reduce this tolerance
save_geojson_print_size(simplified_gdf, output_path)
simplified_gdf.plot()
```

> data/nycc.geojson is 0.18 MB  
> ![Simplified NYC Council Districts](/assets/images/posts/nycc-map/waytoosimple.png)  

And that is way too simplified! `tolerance=10` was too strong.

I found the best tolerance to be `tolerance = 0.000006`. And that's it. Your geojson is ready to use.

```python
simplified_gdf = nycc_gdf.copy()
simplified_gdf["geometry"] = nycc_gdf["geometry"].simplify(tolerance=0.000006, preserve_topology=True)  # reduce this tolerance
save_geojson_print_size(simplified_gdf, output_path)
simplified_gdf.plot()
```

> data/nycc.geojson is 1.98 MB  
> *![Simplified NYC Council Districts](/assets/images/posts/nycc-map/justright.png)
*

From there I just made a simple google sheet with all of the information for the endorsed candidates, including who to also_rank and dont_rank, if valid. Just make sure your first column’s header and formatting exactly match the GeoJSON feature identifier, and that each column uses the same datatype as its corresponding GeoJSON property.

Header and first row below

<div style="overflow-x: auto;">
  <table class="spreadsheet-table">
    <thead>
      <tr>
        <th class="col-district">CounDist</th>
        <th class="col-endorsed">Endorsed</th>
        <th class="col-name">Name</th>
        <th class="col-incumbency">Incumbency</th>
        <th class="col-tagline">Tagline</th>
        <th class="col-photo">Photo URL</th>
        <th class="col-campaign">Campaign URL</th>
        <th class="col-neighborhoods">Neighborhoods</th>
        <th class="col-tooltip">Tooltip Blurb</th>
        <th class="col-also">Also Rank</th>
        <th class="col-dont">Don't Rank</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>1</td>
        <td>TRUE</td>
        <td>Jess Coleman</td>
        <td>Challenger</td>
        <td>Lawyer and Community Activist</td>
        <td><a href="https://i.imgur.com/0I0xwXY.png" target="_blank">Photo Link</a></td>
        <td><a href="https://www.jessfornewyork.com/" target="_blank">Campaign</a></td>
        <td>Battery Park, Financial District, Tribeca, Chinatown, Lower East Side, Soho</td>
        <td>Incumbent Christopher Marte voted against City of Yes, opposed affordable senior housing and safe havens, and fought outdoor dining and congestion pricing.</td>
        <td>Elizabeth Lewinsohn</td>
        <td>Chris Marte</td>
      </tr>
    </tbody>
  </table>
</div>


Connect that as your data source and you can use html to customize the tooltip. 

Datawrapper is an incredibly beautiful free tool for visualizations and it's super easy to use, so I encourage everyone to go play around with it. 

