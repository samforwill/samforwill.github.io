---
layout: single
title: "Voronoi-Based Voter Assignment"
date: 2025-06-30
# categories: [dashboards]
# tags: [python, geopandas, QGIS, tableau]
author_profile: true
classes: wide
# toc: true
# toc_label: "Contents"
# toc_sticky: true

roser:
  - image_path: /assets/images/posts/vc-voronoi/roser-precinct.png
    alt: "Roeser Precinct voter distribution"
    excerpt: "Roeser Precinct"
  - image_path: /assets/images/posts/vc-voronoi/roser-split.png
    alt: "Roeser precinct split across vote centers"
    excerpt: "Roeser Precinct's Closest Vote Centers split"
  - image_path: /assets/images/posts/vc-voronoi/roser-split-bar.png
    alt: "Bar chart showing voter distribution"
    excerpt: "Extent of voter split between Vote Centers"
---
<style>
.page__content {
  font-size: 0.8rem;
}
</style>

## Better Voter Protection Prioritization (Maricopa Example)
*Around 60% of Arizonans (2 million voters) live in Maricopa County, which was served by 256 Vote Centers in the 2024 Election.*

<div class='tableauPlaceholder' id='viz1750525153359' style='position: relative; width: 100%; height: 700px; overflow: hidden; border: 2px solid #ccc; border-radius: 4px;'>
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
    vizElement.style.height = '700px';
    
    var scriptElement = document.createElement('script');
    scriptElement.src = 'https://public.tableau.com/javascripts/api/viz_v1.js';
    vizElement.parentNode.insertBefore(scriptElement, vizElement);
  </script>


### Why I (Re)built This Dashboard
- **Any voter can vote at any polling polling place**  
  Most of Arizona’s 15 Counties, (including its most-populous, Maricopa) use a Vote Center model that lets voters cast ballots at any site in their county of residence, without regard to precinct boundaries.
- **Precinct-distance from Vote Center falls short**  
   The previous way Vote Centers were prioritized was by assigning ALL of a precinct's voters to the closest votecenter based on that precinct's centroid point. This left some polling places overserved and others ignored. 
- **True “nearest” mapping**  
  We needed a way to see which vote centers served the most voters, based on where they actually live, rather than their precinct residence.

### Voronoi-Based Service Areas
By generating Voronoi polygons around all 256 vote-center points and then spatially joining the latitude and longitude of 2 million voters by address, we quickly assign each voter to their true nearest site (without running 2 million × 256 distance checks)

### Exploring the Map

#### Most Populous Precinct - Roeser Precinct
*To fit within Tableau Public’s mark‐count limit, each point on the map represents ~20 voters.*  
Take the most populous precinct in the county, Roeser Precinct. In the previous model, all of its voters would have been assigned to the *Church of Latter Day Saints*. But as you can see, voters in Roeser precinct are split pretty significantly among three nearby vote centers, none of which lie within the precinct itself.
{% include feature_row id="roser"%}


<!-- #### Most Populous Vote Center - Academies at South Mountain
*The Academies at South Mountain* center serves nearly five times more voters than the population of the largest single precinct. But a centroid‐based method could leave it with zero assigned precincts (if no centroid falls closest) or bundle entire precincts arbitrarily, obscuring the true spread of voters it actually serves.
![academies-sm.png](/assets/images/posts/vc-voronoi/academies-sm.png)   -->
<h4>Most Populous Vote Center - Academies at South Mountain</h4>
<div style="display: grid; grid-template-columns: 1fr 2fr; gap: 2rem; align-items: center; margin: 2rem 0;">
  <div>
    <img src="/assets/images/posts/vc-voronoi/academies-sm.png" alt="Academies at South Mountain" style="width: 100%; height: auto;">
  </div>
  <div>
    <p><em>The Academies at South Mountain</em> center serves nearly five times more voters than the population of the largest single precinct. But a centroid‐based method could leave it with zero assigned precincts (if no centroid falls closest) or bundle entire precincts arbitrarily, obscuring the true spread of voters it actually serves.</p>
  </div>
</div>

<!-- Add additional screenshots here as needed -->

### Impact & Takeaways
- **Resource reallocation**  
  Instead of funneling volunteers and legal teams based on precinct proximity, the VoPro team can now focus on the centers actually serving the most people. And by assigning each voter to a Vote Center, we can prioritize the demographic groups we are targeting or serving certain volunteers with language skills to the appropriate places. 
- **Faster, cheaper, scalable**  
  a voronoi spatial join to the lat/longs of only the voters that live within that shape beats millions of distance queries or expensive API calls.

---

## Details & Methodology

- **Data workaround**  
  Because the Arizona voter file is not publicly availalbe, this tableau dashboard demonstration uses a parcel point workaround: Maricopa County parcel points were randomly labeled Democrat or Republican based on each precinct’s 2024 vote share. Parcel points are from [Maricopa GIS Open Data](https://data-maricopa.opendata.arcgis.com/datasets/dbf139379db946e1b10a2f15672c142d/about), and the precinct-level results come from the [NYT 2024 GitHub repository](https://github.com/nytimes/presidential-precinct-map-2024).


---


