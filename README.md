![logo](BR_Black.jpg)
# WORKSHOP - Sharing data with eMOTIONAL Cities SDI
The purpose of workshop is to learn how-to use the eMOTIONAL Cities Spatial Data Infrastructure (SDI). Please read the [FAQ](#FAQ-:question:) section for more information.
This workshop was created by [ByteRoad](https://byteroad.net/), in the context of the [eMOTIONAL Cities](https://emotionalcities-h2020.eu/) project.

## Architecture and Technology Stack
The SDI uses an hybrid architecture, with a mix of [legacy](#the-legacy-stack) and [newer](#the-modern-stack) OGC standards. On one hand we will leverage the OGC API family of standards, which are web native and present a number of advantages for modern web applications. On the other hand, we aknoweledge the fact that a certain degree of compatibility with legacy OGC Web Services (OWS) may be required for some use cases, and will publish data also using those standards.

### The Modern Stack
These are the standards that we identified as relevant for publishing the eMOTIONAL Cities datasets:
- OGC API Features - for serving feature data over the web;
- OGC API Tiles - for serving vector tiles over the web;
- OGC API Records - for exposing a catalogue of geospatial metadata;
- OGC API DGGS - for serving data organised according to a Discrete Global Grid System (for instance, indexes);

> **Note**
> Add hyperlinks to the standards above

### The Legacy Stack
The legacy stack rests on the solid foundation of GeoServer, which allows geospatial datasets to be exposed in the following standards:
- WFS 1.0.0, 1.1.0, 2.0.0
- WMS 1.1.1, 1.3.0
- WMS-C 1.1.1
- WMTS 1.0.0

> **Note**
> Add hyperlinks to the standards above

## Where is the SDI?
You can access the ```newer``` SDI at this endpoint:

https://emotional.byteroad.net/

It features a HTML interface, which you can use to explore it.

View the list of available collections, by clicking on ```View the collections in this service```, or by accessing this endpoint:

https://emotional.byteroad.net/collections?f=html

You can click in any collection, to learn about the available services and access the data.

You can access the ```legacy``` SDI at this endpoint:

https://oldskool.byteroad.net/geoserver/

The UI is protected with username and password, so ask for the credentials first.

These are the endpoints for the different services:
- [WMS 1.3.0](http://localhost/geoserver/ows?service=wms&version=1.3.0&request=GetCapabilities)
- [WMTS 1.0.0](http://localhost/geoserver/gwc/service/wmts?REQUEST=GetCapabilities)
- [WFS 2.0.0](http://localhost/geoserver/ows?service=wfs&version=2.0.0&request=GetCapabilities)

> **Note**
> Add missing datasets to the legacy SDI.

Browse the catalogue using this client:

https://github.com/Luoghi-indomiti/bootstrap-ogc-api-react

> **Note**
> Enable GitHub pages for this endpoint and replace the link.

## Connecting to the SDI using a Client
Using the endpoints above, you can access data from the SDI using a client, provided that the client supports the standards in the [legacy](#the-legacy-stack) or [newer](#the-modern-stack). In this section of the workshop, we will demonstrate how-to do that, using different clients: QGIS, python/OWSLib, Mapstore and JavaScript/LeafLet. If you are using a different GIS client, you can ask us if it has support for any of these standards.

### QGIS
> **Note**
> OGC API Features, OGC API Vector Tiles, OGC API Records, OGC WFS, WMTS & WMTS.

### Mapstore
> **Note**
> OGC WFS, WMTS & WMTS.

### Python
> **Note**
> OGC API Features, OGC API Records, OGC WFS, WMTS & WMTS.

### JavaScript
> **Note**
> OGC API Features, OGC API Vector Tiles

## Authoring Metadata
> **Warning**
> Use QGIS & PygeoMeta?

## Ingesting Data into the SDI
> **Note**
> Let participants upload data to the data lake. 

> **Warning**
> We ingest these data in the SDI and let them connect to it ?

## FAQ :question:

**Q: How can I register for the workshop?**

**A:** Please register using [this](https://docs.google.com/forms/d/e/1FAIpQLSffKGPfxnrFIAVHXUDnkUDzrWAn7a-YNTHgkWuwVnGTCWbQ6Q/viewform) link.

**Q: Do I need to install anything ahead of the workshop?**

**A:** Yes. If you want to be *hands-on*, please install (*at least, some of*) this software:
- QGIS
- Jupyter
- Visual Studio Code or another text editor

> **Note**
> Provide installation instructions.

**Q: Is this workshop for me?**

**A:** If you produce/collect or access any data from the eMOTIONAL Cities project, this workshop is for you.

**Q: Do I need to know how-to code, in order to attend this workshop?**

**A:** No. Although some of the client applications which interface with the SDI use some coding, we will also show *no-coding* alternatives.

**Q: What will I learn during this workshop?**

**A:** At the end of this workshop you should be able to consume data from the SDI using a client and ingest data to the SDI, through the data lake.




