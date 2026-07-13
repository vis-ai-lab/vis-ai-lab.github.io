---
layout: default

year: 2023
title: "Multi-view Design Patterns and Responsive Visualization for Genomics Data"
image: multi-view-design-patterns-and.png
featured: false 

authors:
    - Sehi L'Yi
    - Nils Gehlenborg

types:
    - conference
    - journal

tags:
    - visualization
    - genomics
    - gosling

venue_name_short: TVCG
venue_name: IEEE Transactions on Visualization and Computer Graphics (TVCG) (Proc. VIS)
venue_index: 29(1), 559-569
acceptance_rate: 26.5

publisher_url: https://ieeexplore.ieee.org/document/9904451
demo_url: https://gosling.js.org
code_url: https://github.com/gosling-lang/gosling.js
slideshare_key: hA2YdbV27diNbd
talk_venue: Paper Presentation @ VIS 2022
---

A series of recent studies has focused on designing cross-resolution and cross-device visualizations, i.e., responsive visualization, a concept adopted from responsive web design. However, these studies mainly focused on visualizations with a single view to a small number of views, and there are still unresolved questions about how to design responsive multi-view visualizations. In this paper, we present a reusable and generalizable framework for designing responsive multi-view visualizations focused on genomics data. To gain a better understanding of existing design challenges, we review web-based genomics visualization tools in the wild. By characterizing tools based on a taxonomy of responsive designs, we find that responsiveness is rarely supported in existing tools. To distill insights from the survey results in a systematic way, we classify typical view composition patterns, such as “vertically long,” “horizontally wide,” “circular,” and “cross-shaped” compositions. We then identify their usability issues in different resolutions that stem from the composition patterns, as well as discussing approaches to address the issues and to make genomics visualizations responsive. By extending the Gosling visualization grammar to support responsive constructs, we show how these approaches can be supported. A valuable follow-up study would be taking different input modalities into account, such as mouse and touch interactions, which was not considered in our study.
