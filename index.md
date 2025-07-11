---
title: "Data for Strategy and Impact"
about: "Data Portfolio and Personal Website"     
layout: single
permalink: /
classes: wide
author_profile: true
       
sidebar:
  - title: "Skills"
    text: |
      **Python:** pandas, numpy, requests, web scraping, data analysis  
      **SQL:**  dbt, ETL/ELT, BigQuery  
      **Dashboards:** Hex, Looker Studio, Tableau, Streamlit  
      **Visualization:** matplotlib, seaborn, Plotly, Bokeh, Datawrapper  
      **Machine Learning:** scikit-learn (regression, classification)  
      **Geospatial:** GeoPandas, QGIS  
      **Campaign Data:** NGPVAN, Mobilize, Civis, Parsons  
      **Collaboration:** Git, Asana, Google Workspace, Jupyter
 
header:
  tagline: "Welcome to My Site"
  actions:
    - label: "Get Started"
      url: "#features"
    - label: "Learn More"
      url: "/about/"
excerpt:  
intro:
  - excerpt: >
      Hi, I'm Forrest, a Data Analyst based in Queens, NY.  
  
  
      I started my career in non-profit immigrant advocacy, then after several years with the Census Bureau, my path led me to Arizona where I was Deputy Data Director for the AZ Democrats/Harris for President campaign. I put this site together to show off some of my projects, tools, and skills I've learned along the way.  (And I'll probably post some personal tidbits, like my half year in Uruguay and Cuba following the 2024 cycle.)   
  

      Scroll down to see some (mostly) interactive snippets of my work. And click through any project to explore the data, code, and process behind it.
  

feature_row:
  - image_path: "/assets/images/Deluzio_For_Congress_Banner.png"
    alt: "NLP Campaign Messaging"
    title: "NLP Campaign Messaging"
    excerpt: "Examining candidate messaging strategies with topic modeling and clustering."
    url: "https://samforwill.github.io/nlp-campaign-messaging/"
    btn_label: "View Project"
    btn_class: "btn--info"

  - image_path: "/assets/images/Redistricting_Type_Composite.png"
    alt: "Demographics and Partisan Lean"
    title: "Demographics & Partisan Lean"
    excerpt: "Predicting district PVI from demographic data using regression models."
    url: "https://samforwill.github.io/predict-cd-pvi/"
    btn_label: "View Project"
    btn_class: "btn--info"

  - image_path: "/assets/images/4- Shifted Predicted Composition State Senates.png"
    alt: "State Legislative Districts PVI"
    title: "State Leg. Districts PVI"
    excerpt: "Mapping state‐leg maps and PVI using GeoPandas and interactive visuals."
    url: "https://samforwill.github.io/sldu-pvi/"
    btn_label: "View Project"
    btn_class: "btn--info"

---

<!--STYLE: Pulls the body left so that author_toc doesn't take up so much space-->
<!-- also resets the negative margin for mobile-->
<style>
.sidebar {
  width: 230px !important;
}
.page__content {
  margin-left: -50px !important;
  max-width: calc(100% - 20px) !important;
}
.page__title {
  margin-left: -50px !important;
}
@media (max-width: 768px) {
  .sidebar, .page__content {
    width: 100% !important;
    margin-left: 0 !important;
    max-width: 100% !important;
  }
  .page__title {
    margin-left: 0 !important;
  }
  div[style*="grid-template-columns"] {
    display: block !important;
  }
  div[style*="grid-template-columns"] > div {
    margin-bottom: 1rem;
  }
}
</style>

{% include feature_row id="intro" type="" %}
<h1 style="
  text-align: center;
  text-decoration: underline;
  margin: 0rem 1;
">
  Recent Posts
</h1>

<!-- Video Section - Add this above your existing map section -->
<div style="margin-bottom: 2rem;">
  <h3>[Hex] Vote Locations & Voter Universe Dashboard – Apache, Navajo, and Pima Counties</h3>
  <p>This dashboard powered the VoPro Team's polling site and dropbox strategy across three key Arizona counties with significant Tribal populations. It was used to urge county Boards of Supervisors to expand polling locations ahead of the Early Vote deadline.</p>
  
  <iframe src="https://drive.google.com/file/d/1iJbMXwiCD4wRsSvMrOAAl_7e2twkfgmK/preview" 
          width="100%" 
          height="480" 
          style="max-width: 800px; border: none; box-shadow: 0 6px 20px rgba(0,0,0,0.25);"
          allow="autoplay">
  </iframe>
</div>

<!-- Dividing Line-->
<hr style="margin: 1.5rem 0; border: 0; height: 2px; background: #d1d5da;">

<!-- 1) DATAWRAPPER MAP – Plot | Text -->
<div style="display: grid; grid-template-columns: 35% 65%; gap: 1.5rem; margin-bottom: 2rem;">
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
    <h3>Abundance NY City Council Endorsements Map</h3>
    <p>I made this for Abundance NY ahead of the NYC primaries to share a fun infograph of councilor endorsements, especially for down-ballot races where people may not know the candidates as well. This was mostly an excuse to use Datawrapper, since it is so universally beloved (for good reason!). </p> 
    
    <p>This was a quick map to build, but I did have to simplify geometries with GeoPandas and convert the shapefile for use in Datawrapper. It also got a lot of views!</p>

    <p> Click through to see the full process. </p>
    <a href="https://samforwill.github.io/2025/06/27/abundance-endorsements.html" class="btn btn--info btn--large">Visit Full Post</a>
  </div>
</div>

<!-- Dividing Line-->
<hr style="margin: 1.5rem 0; border: 0; height: 2px; background: #d1d5da;">

<!-- 2): MGP TOPIC SCATTER PLOT -->
<h3>Natural Language Processing and Campaign Messaging Strategy</h3>

<div style="display:grid; grid-template-columns:70% 30%; gap:1.5rem; align-items:start;margin-bottom: 1rem;">
  <!-- Left: iframe -->  
  <a href="https://samforwill.github.io/nlp-campaign-messaging" style="display: block; text-decoration: none;">
    <div style="position:relative;padding-bottom:100%;height:0;overflow:hidden;box-shadow: 0 6px 20px rgba(0,0,0,0.25);">
      <iframe
        src="/assets/plots/interactive/mgp_topic_scatter1.html"
        style="position:absolute;top:6%;left:0;width:100%;height:100%;border:0;"
        allowfullscreen>
      </iframe>
    </div>
  </a>
  <!-- Right: text --> 
  <div style="font-size: 0.9em;">
    <p style="margin-bottom: 2rem; margin-top: 1rem"> I used topic modeling (NMF) to analyze social media posts from <b>Marie Gluesenkamp-Perez (WA-03)</b> and <b>Chris Deluzio (PA-17)</b>, based on their 2022 campaigns.</p>
    
    <p>This Bokeh scatterplot clusters MGP's tweets by topic to highlight patterns in messaging strategy.</p>

    <p style="margin-bottom: 1.5rem; margin-top: 1.5rem"> Hover over points to read individual tweets within each topic. </p>

  </div>
</div>

<!-- 3): text on left, CANDIDATE COMPARISON BARPLOT on right -->
<div style="display: grid; grid-template-columns: 30% 70%; gap: 1.5rem; margin-bottom: 2rem;">
  <!-- Left: text -->
  <div style="font-size: 0.9em;">
    <p style="margin-bottom: 1.5rem; margin-top: 1.5rem">At the end of the project, I compared topic frequencies between the two candidates using a Twitter-trained GloVe model.</p> 
    <p>This chart (also Bokeh) compares how often each candidate tweeted about key themes to highlight overlaps and differences in their messaging.</p>
    <a href="https://samforwill.github.io/nlp-campaign-messaging/" class="btn btn--info btn--large">Visit Full Project Page</a>
  </div>
  <!-- Right: iframe -->
  <div style="position:relative; padding-bottom:100%; height:0; overflow:hidden;box-shadow: 0 6px 20px rgba(0,0,0,0.25);">
    <iframe
      src="/assets/plots/interactive/candidate_topic_barplot1.html"
      style="position:absolute; top:3%; left:3%; width:100%; height:100%; border:0;"
      allowfullscreen>
    </iframe>
  </div>
</div>

<!-- Dividing Line-->
<hr style="margin: 1.5rem 0; border: 0; height: 2px; background: #d1d5da;">



<!-- 3) Full-width TABLEAU DASHBOARD-->
<div style="margin-bottom:2rem;">
    <p style="margin-top: 1rem; text-align:center;">
    <strong>Maricopa Precinct v Closest Votecenter Dashboard</strong><br>
    </p>
    <p style="text-align:left;">
    This interactive dashboard plots each voter against the nearest of 256 vote centers, exposing how precinct‐level aggregation misallocates resources in an open votecenter system. It supported the Voter Protection team in directing limited volunteer and legal resources to the centers where they were needed most in 2024 General Election.<br><br>

    Click through to learn more about the process and purpose of making this dashboard.
    </p>
  <div style="text-align: center;">
  <a href="https://samforwill.github.io/2025/06/30/votecenter-voronoi.html" class="btn btn--info btn--large">Visit Full Post</a>
  </div>
  
  <div class='tableauPlaceholder' id='viz1750525153359' style='position: relative; width: 100%; height: 700px; overflow: hidden; box-shadow: 0 6px 20px rgba(0,0,0,0.25);'>
    <noscript>
      <a href='#'>
        <img alt='Dashboard 1' src='https://public.tableau.com/static/images/Ma/MaricopaCountyPrecinctv_VoteCenterAggregation/Dashboard1_rss.png' style='border: none; width:100%;' />
      </a>
    </noscript>
    <object class='tableauViz' style='display:none; width:100%; height:700px; overflow: hidden;'>
      <param name='host_url' value='https%3A%2F%2Fpublic.tableau.com%2F' />
      <param name='embed_code_version' value='3' />
      <param name='site_root' value='' />
      <param name='name' value='MaricopaCountyPrecinctv_VoteCenterAggregation/Dashboard1' />
      <param name='tabs' value='no' />
      <param name='toolbar' value='yes' />
      <param name='static_image' value='https://public.tableau.com/static/images/Ma/MaricopaCountyPrecinctv_VoteCenterAggregation/Dashboard1/1.png' />
      <param name='animate_transition' value='yes' />
      <param name='display_static_image' value='yes' />
      <param name='display_spinner' value='yes' />
      <param name='display_overlay' value='yes' />
      <param name='display_count' value='yes' />
      <param name='language' value='en-US' />
      <param name='showVizHome' value='no' />
      <param name='scrollbars' value='no' />
    </object>
  </div>
  <script>
    var divElement = document.getElementById('viz1750525153359');
    var vizElement = divElement.getElementsByTagName('object')[0];
    
    vizElement.style.width = '100%';
    vizElement.style.height = '850px';
    
    var scriptElement = document.createElement('script');
    scriptElement.src = 'https://public.tableau.com/javascripts/api/viz_v1.js';
    vizElement.parentNode.insertBefore(scriptElement, vizElement);
  </script>
</div>




