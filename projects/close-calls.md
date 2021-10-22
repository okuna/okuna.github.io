---
layout: project
type: project
image: images/close-calls/close-calls.png
title: Close Calls (Insight Data Engineering)
permalink: projects/close-calls
# All dates must be YYYY-MM-DD format!
date: 2020-08-01
labels:
  - Big Data
  - Apache Spark
  - MySQL
summary: Big data patching pipeline and visualization for >500GB of ATC data 
---

<div style="position: relative; width: 100%; height: 0; padding-bottom: 56.25%; ">
  <iframe style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;" src="https://www.youtube.com/embed/_ZoLmJV6aUo" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>

Close Calls is a data engineering project combining an Apache Spark batching pipeline and a custom visualization using Google Maps and Aurelia to display near-misses of worldwide air traffic. The data source was roughly 80GB/day of JSON files from adsb-exchange.com. In total, I had around 500 GB of data and was able to process it all in faster than real time. 