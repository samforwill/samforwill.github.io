---
title: "Portfolio"
about: "my data portfolio"     
layout: single
permalink: /
classes: wide

       

 
header:
  tagline: "Welcome to My Site"
  actions:
    - label: "Get Started"
      url: "#features"
    - label: "Learn More"
      url: "/about/"
excerpt:  
intro:
  - excerpt: Forrest Williams is a New York-based data analyst and election specialist who turns complex political and social data into clear, interactive visual stories. He builds dynamic dashboards—from campaign‐messaging scatter plots to district‐level endorsement maps—that make insights easy to explore. When he’s not working with election data, he’s refining Jekyll themes and pushing the boundaries of web-based visualizations to make data both beautiful and accessible.

feature_row:
  - image_path: /assets/images/placeholder.jpg
    alt: "Placeholder one"
    title: "Feature One"
    excerpt: "This is the first feature."
  - image_path: /assets/images/placeholder.jpg
    alt: "Placeholder two"
    title: "Feature Two"
    excerpt: "This is the second feature."
  - image_path: /assets/images/placeholder.jpg
    alt: "Placeholder three"
    title: "Feature Three"
    excerpt: "This is the third feature."

feature_row2:
  - image_path: /assets/images/placeholder.jpg
    alt: "placeholder image 2"
    title: "Placeholder Image Left Aligned"
    excerpt: 'This is some sample content that goes here with **Markdown** formatting. Left aligned with `type="left"`'
    url: "#test-link"
    btn_label: "Read More"
    btn_class: "btn--primary"
footer_content: |
  <p>© {{ site.time | date: "%Y" }} Samuel Williams</p>
---

<!--STYLE: Pulls the body left so that the author profile doesn't take up so much space-->
<!-- also resets the negative margin for mobile-->
<style>
.sidebar {
  width: 200px !important;
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


<h2 style="
  text-align: center;
  text-decoration: underline;
  margin: 2rem 0;
">
  Interactive Plots and Dashboards
</h2>
<!-- Dividing Line-->
<hr style="margin: 1.5rem 0; border: 0; height: 2px; background: #d1d5da;">

<!-- First plot: MGP TOPIC SCATTER PLOT on left, text on right -->
<div style="display:grid; grid-template-columns:70% 30%; gap:1.5rem; align-items:start;">
  <!-- Left: iframe -->  
  <div>
    <div style="position:relative;padding-bottom:100%;height:0;overflow:hidden;box-shadow: 0 6px 20px rgba(0,0,0,0.25);">
      <iframe
        src="/plots/static/mgp_topic_scatter1.html"
        style="position:absolute;top:6%;left:0;width:100%;height:100%;border:0;"
        allowfullscreen>
      </iframe>
    </div>
  </div>
  <!-- Right: text --> 
  <div>
    <h3>Topic Scatter</h3>
    <p>Interactive topic-model scatter plot.</p>
  </div>
</div>

<!-- Dividing Line-->
<hr style="margin: 1.5rem 0; border: 0; height: 2px; background: #d1d5da;">

<!-- Second plot: text on left, CANDIDATE COMPARISON BARPLOT on right -->
<div style="display: grid; grid-template-columns: 30% 70%; gap: 1.5rem; margin-bottom: 2rem;">
  <!-- Left: text -->
  <div>
    <h3>Topic Comparisons</h3>
    <p>Barplot showing relative topic–tweet frequencies for each candidate.</p>
  </div>
  <!-- Right: iframe -->
  <div style="position:relative; padding-bottom:100%; height:0; overflow:hidden;box-shadow: 0 6px 20px rgba(0,0,0,0.25);">
    <iframe
      src="/plots/static/candidate_topic_barplot1.html"
      style="position:absolute; top:3%; left:3%; width:100%; height:100%; border:0;"
      allowfullscreen>
    </iframe>
  </div>
</div>

<!-- Dividing Line-->
<hr style="margin: 1.5rem 0; border: 0; height: 2px; background: #d1d5da;">

<!-- 3) DATAWRAPPER MAP – Plot | Text -->
<div style="display: grid; grid-template-columns: 35% 65%; gap: 1.5rem; margin-bottom: 2rem;">
  <!-- Left: Datawrapper -->
  <div style="position:relative; max-width:100%; overflow: visible; box-shadow: 0 6px 20px rgba(0,0,0,0.25);">
    <iframe
      title="NYC Endorsements Map"
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
    <h3>NYC Endorsements Map</h3>
    <p>Interactive Datawrapper map of endorsements across City Council districts.</p>
  </div>
</div>

<!-- Dividing Line-->
<hr style="margin: 1.5rem 0; border: 0; height: 2px; background: #d1d5da;">

<!-- 3) Full-width TABLEAU DASHBOARD-->
<div style="margin-bottom:2rem;">
  <div class='tableauPlaceholder' id='viz1750525153359' style='position: relative; width: 100%; height: 700px; overflow: hidden;'>
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
    
    vizElement.style.width = '110%';
    vizElement.style.height = '850px';
    
    var scriptElement = document.createElement('script');
    scriptElement.src = 'https://public.tableau.com/javascripts/api/viz_v1.js';
    vizElement.parentNode.insertBefore(scriptElement, vizElement);
  </script>

  <p style="margin-top: 1rem; text-align:center;">
    <strong>Precinct–Vote Center Dashboard</strong><br>
    Tableau Public visualization of vote center aggregation by precinct.
  </p>
</div>


{% include feature_row %}