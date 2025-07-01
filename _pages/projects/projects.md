---
title: "Projects"
permalink: /projects/
layout: single
author_profile: true
classes: wide
header:
  overlay_color: "#000"
  overlay_filter: "0.5"
  excerpt: "A collection of data science and political analysis projects"

intro: 
  - excerpt: "These projects showcase my work in political data analysis, natural language processing, and predictive modeling. Each project represents a deep dive into different aspects of electoral politics and demographic analysis."

feature_row:
  - image_path: "/assets/images/Deluzio_For_Congress_Banner.png"
    alt: "NLP Campaign Messaging"
    title: "NLP Campaign Messaging"
    excerpt: "Examining candidate messaging strategies with topic modeling and clustering to understand political communication patterns and voter engagement tactics."
    url: "https://samforwill.github.io/nlp-campaign-messaging/"
    btn_label: "View Project"
    btn_class: "btn--primary"

  - image_path: "/assets/images/Redistricting_Type_Composite.png"
    alt: "Demographics and Partisan Lean"
    title: "Demographics & Partisan Lean"
    excerpt: "Predicting district PVI from demographic data using regression models to understand the relationship between community composition and voting patterns."
    url: "https://samforwill.github.io/predict-cd-pvi/"
    btn_label: "View Project"
    btn_class: "btn--primary"

  - image_path: "/assets/images/4- Shifted Predicted Composition State Senates.png"
    alt: "State Legislative Districts PVI"
    title: "State Legislative Districts PVI"
    excerpt: "Mapping state legislative districts and calculating PVI using GeoPandas and interactive visualizations to analyze political geography at the state level."
    url: "https://samforwill.github.io/sldu-pvi/"
    btn_label: "View Project"
    btn_class: "btn--primary"
---

{% include feature_row id="intro" type="center" %}

{% include feature_row %}