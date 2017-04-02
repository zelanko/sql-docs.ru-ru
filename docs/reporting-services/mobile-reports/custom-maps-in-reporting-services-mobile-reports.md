---
title: "Custom maps in Reporting Services mobile reports | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 59a4ebad-587a-4770-afcd-c69216b8afd9
caps.latest.revision: 9
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 8
---
# Custom maps in Reporting Services mobile reports
Географические карты в [!INCLUDE[PRODUCT_NAME](../../includes/product-name.md)] определяются в формате, известном как *файлы фигур ESRI*.  
  
Этот формат, первоначально разработанный частной компанией, теперь является широко распространенным частично открытым форматом, используемым во многих приложениях GIS. В соответствии с этим форматом для [!INCLUDE[PRODUCT_NAME](../../includes/short-product-name.md)] требуется два файла, чтобы определить карту:  
  
- SHP-файл для контуров фигур  
- DBF-файл для метаданных  
  
Базовые имена файлов должны совпадать (например, *canada.shp* и *canada.dbf*). Метаданные должны включать поле *NAME* со значением соответствующего имени фигуры (ключа), которое будет использоваться при заполнении карты данными.  
  
> **Примечание**. Два файла карты вместе, SHP и DBF, по размеру не должны превышать 512 КБ. Если файлы карты слишком велики, для уменьшения их размера можно воспользоваться таким инструментом, как [http://mapshaper.org/](http://mapshaper.org/).  
  
Узнайте, как [добавлять пользовательские карты в мобильные отчеты](../../reporting-services/mobile-reports/add-a-custom-map-to-a-reporting-services-mobile-report.md).  
  
## Технические сведения  
  
- Официальная спецификация: [http://www.esri.com/library/whitepapers/pdfs/shapefile.pdf](http://www.esri.com/library/whitepapers/pdfs/shapefile.pdf)  
- Статья Википедии, посвященная файлам фигур: [http://en.wikipedia.org/wiki/Shapefile](http://en.wikipedia.org/wiki/Shapefile)  
  
## Создание и редактирование геометрии карты  
  
Создание и редактирование файлов фигур является сложным процессом, описание которого выходит за рамки данного документа. Ниже приведены некоторые ресурсы и приложения, которые помогут вам приступить к работе.  
  
- ArcGIS: [http://www.arcgis.com/](http://www.arcgis.com/)  
- Подключаемый модуль MAPublisher для Adobe Illustrator: [http://www.avenza.com/mapublisher](http://www.avenza.com/mapublisher)  
- QuantumGIS (бесплатно): [http://www.qgis.org/](http://www.qgis.org/)  
- Manco ShapeFile Editor: [http://www.mancosoftware.com/ShapeFileEditor](http://www.mancosoftware.com/ShapeFileEditor)  
  
## Существующие файлы фигур  
  
Многие существующие файлы фигур можно скачать с веб-сайтов, таких как:  
  
- Diva GIS: [http://www.diva-gis.org/Data](http://www.diva-gis.org/Data)  
- OpenStreetMap: [http://openstreetmapdata.com/data](http://openstreetmapdata.com/data)  
- GeoCommons: [http://www.geocommons.com/](http://www.geocommons.com/)  
  
### См. также:  
- [Maps in Reporting Services mobile reports](../../reporting-services/mobile-reports/maps-in-reporting-services-mobile-reports.md)  
- [Создание и публикация мобильных отчетов с помощью издателя мобильных отчетов SQL Server](../../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md)   
  
  
  
