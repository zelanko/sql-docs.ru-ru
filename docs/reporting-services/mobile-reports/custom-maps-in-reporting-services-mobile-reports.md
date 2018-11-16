---
title: Пользовательские карты в мобильных отчетах Reporting Services | Документы Майкрософт
ms.date: 03/30/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: mobile-reports
ms.topic: conceptual
ms.assetid: 59a4ebad-587a-4770-afcd-c69216b8afd9
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: a3786fcf92c767905c6295dffc8a24e7a86d2cbe
ms.sourcegitcommit: 9ece10c2970a4f0812647149d3de2c6b75713e14
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51813947"
---
# <a name="custom-maps-in-reporting-services-mobile-reports"></a>Custom maps in Reporting Services mobile reports
Географические карты в издателе мобильных отчетов для SQL Server определяются в формате, известном как *файлы фигур ESRI*.  
  
Этот формат, первоначально разработанный частной компанией, теперь является широко распространенным частично открытым форматом, используемым во многих приложениях GIS. В соответствии с этим форматом для издателя мобильных отчетов требуется два файла, чтобы определить карту:  
  
- SHP-файл для контуров фигур  
- DBF-файл для метаданных  
  
Базовые имена файлов должны совпадать (например, *canada.shp* и *canada.dbf*). Метаданные должны включать поле *NAME* со значением соответствующего имени фигуры (ключа), которое будет использоваться при заполнении карты данными.  
  
> **Примечание**. Два файла карты вместе, SHP и DBF, по размеру не должны превышать 512 КБ. Если файлы карты слишком велики, для уменьшения их размера можно воспользоваться таким средством, как [https://mapshaper.org/](https://mapshaper.org/).  
  
Узнайте, как [добавлять пользовательские карты в мобильные отчеты](../../reporting-services/mobile-reports/add-a-custom-map-to-a-reporting-services-mobile-report.md).  
  
## <a name="technical-information"></a>Технические сведения  
  
- Официальная спецификация: [https://www.esri.com/library/whitepapers/pdfs/shapefile.pdf](https://www.esri.com/library/whitepapers/pdfs/shapefile.pdf)  
- Статье о файлах фигур в Википедии: [https://en.wikipedia.org/wiki/Shapefile](https://en.wikipedia.org/wiki/Shapefile)  
  
## <a name="creating--editing-map-geometry"></a>Создание и редактирование геометрии карты  
  
Создание и редактирование файлов фигур является сложным процессом, описание которого выходит за рамки данного документа. Ниже приведены некоторые ресурсы и приложения, которые помогут вам приступить к работе.  
  
- ArcGIS: [https://www.arcgis.com/](https://www.arcgis.com/)  
- Подключаемый модуль MAPublisher для Adobe Illustrator: [https://www.avenza.com/mapublisher](https://www.avenza.com/mapublisher)  
- QuantumGIS (бесплатно): [https://www.qgis.org/](https://www.qgis.org/)  
- Редактор Manco файлов фигур: [https://www.mancosoftware.com/ShapeFileEditor](https://www.mancosoftware.com/ShapeFileEditor)  
  
## <a name="existing-shapefiles"></a>Существующие файлы фигур  
  
Многие существующие файлы фигур можно скачать с веб-сайтов, таких как:  
  
- Diva-GIS: [https://www.diva-gis.org/Data](https://www.diva-gis.org/Data)  
- OpenStreetMap: [https://openstreetmapdata.com/data](https://openstreetmapdata.com/data)  
  
### <a name="see-also"></a>См. также раздел  
- [Maps in Reporting Services mobile reports](../../reporting-services/mobile-reports/maps-in-reporting-services-mobile-reports.md)  
- [Создание и публикация мобильных отчетов с помощью издателя мобильных отчетов SQL Server](../../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md)   
  
  
  
