---
title: "Launching GeoDownloader.com: Simplifying OpenStreetMap Data Downloads"
date: 2025-01-02
tags: 
  - "arcgis"
  - "geojson"
  - "geopackage"
  - "geospatial"
  - "gis"
  - "mapping"
  - "opensource"
  - "openstreetmap"
  - "osm"
  - "qgis"
  - "shapefile"
---

I’m excited to share my new project I’ve been working on: **[GeoDownloader.com](https://geodownloader.com/)**, a tool I built to make downloading [OpenStreetMap](https://www.openstreetmap.org/) (OSM) data easier and more intuitive than other website I have been used so far. If you’ve ever struggled with getting the right geospatial data in the right format for your project, I think you’ll find this project useful too.

## Why I Created GeoDownloader.com

Working with [OpenStreetMap](https://www.openstreetmap.org/) data is incredibly rewarding for geospatial projects, but it can also be frustrating. The data is rich and comprehensive, but accessing it in a way that fits your project's needs can be time-consuming. I've personally spent hours wrestling with overly complex workflows, converting file formats, and extracting specific data from larger datasets. While there are websites that help you download data, I don't find them intuitive. Thus, I decided to build another one to make it easier for myself and anyone else who faces similar challenges.

Downloading data for a specific area with a small number of features can be particularly time-consuming. There are several options for downloading data through GIS applications like QGIS, but I wanted to create something that runs in your browser for small tasks (for now 😉).

That's how [**GeoDownloader.com**](https://geodownloader.com) was born – a website where you can quickly download exactly the data you need, in the format you need, without any unnecessary hassle.

## How to use

I've designed GeoDownloader with a simple and approachable interface, making it easy for users new to GIS or [OpenStreetMap](https://www.openstreetmap.org/) to start downloading data immediately.

<!--more-->

The intuitive map interface allows you to visually select your **_area of interest (AOI)_**. Simply draw a shape on the map, and GeoDownloader will automatically capture all features within that boundary.

You can easily customize your download by deselecting any unwanted features from the list, ensuring you only get the data you need.

Understanding the importance of compatibility in GIS workflows, GeoDownloader supports exports in three formats:

- GeoPackage

- Shapefile

- GeoJSON

Choose the format that best suits your tools, whether you're using QGIS, ArcGIS, or other software. Let me know in the comments if you need additional format options.

### **Filtering Tools**

One of my favorite features is the ability to **filter selected data**. You can refine your selection based on:

- **Tags:** Select features by OSM tags like `highway`, `building`, or `landuse`.

- **Tag Values:** Narrow down by specific tag values, such as `highway=primary` or `building=school`.

- **Geometry Type:** Focus on specific geometry types, like points, lines, or polygons.

These filters give you precise control over what you’re downloading, saving you the effort of cleaning or preprocessing data later.

## Limits

There are some important limitations I need to explain. I created this tool to simplify downloading small datasets from OpenStreetMap, but there are certain constraints. Instead of proxying third-party APIs like [Overpass API](https://wiki.openstreetmap.org/wiki/Overpass_API), I host all OSM data on my server in an indexed format. This approach ensures you can access the data without restrictions from external services. Additionally, I wanted to avoid creating extra load on the free Overpass API.

Hosting OSM data on my server involves costs that I need to cover, so I charge a small fee for downloading more than 100 features. If the website gains more users, I may be able to reduce this price, as my goal isn't to profit significantly from this service. 😊🤑

## What’s Next for GeoDownloader.com

While I’m thrilled with how far GeoDownloader has come, I see this as just the beginning. Here’s what I’m planning next:

- Adding support for more file formats and data sources.

- Enhancing the filtering options with more granular controls.

- Increasing data limits for each package.

If you have ideas or features you’d like to see, I’d love to hear from you!

## What I've learnt from this

Throughout the development of GeoDownloader.com, I gained invaluable experience and knowledge in handling OpenStreetMap (OSM) raw data. Here are some key takeaways from this journey:

1. **Dealing with OSM Raw Data**: I learned how to efficiently manage and process raw OSM data. This involved understanding the structure of OSM data and file format (PBF).

3. **Converting Data with GDAL and Python**: I utilized GDAL (Geospatial Data Abstraction Library) and Python to convert OSM data into an indexable format. This process included writing scripts to automate data conversion and ensuring the data was ready for further analysis and use.

5. **Using GeoPandas for Data Conversion**: I explored GeoPandas, a powerful Python library, to convert the processed data into various formats. GeoPandas made it easier to handle geospatial data and perform complex operations, such as reprojecting and merging datasets.

7. **Building UI with AI Tools**: I learned how to use AI tools, specifically Claude AI, to build user interfaces faster and more professionally. This significantly improved the efficiency and quality of the UI development process.

9. **Integrating Stripe for Payments**: As the server cost is too high to cover myself, I learned how to integrate Stripe to collect a small fee to cover these costs for large data sets. This integration was crucial for maintaining the sustainability of the project.

11. **Using Tailwind CSS for Frontend Development**: Although I am primarily a back-end developer and do not do much front-end coding in my daily job, I used the Tailwind CSS framework to build the UI. I found its ready-to-use class names extremely useful and efficient for developing interfaces.

## Try It Out

GeoDownloader.com is live now, and I’d be honored if you gave it a try. I hope it makes your work with OpenStreetMap data faster, easier, and more enjoyable.

Head over to [GeoDownloader.com](https://geodownloader.com/) and let me know what you think.
