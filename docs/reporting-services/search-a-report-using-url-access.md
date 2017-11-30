---
title: "Поиск отчета с использованием URL-адресов | Документы Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- searching reports
- text searches [Reporting Services]
- URL access [Reporting Services], report searches
ms.assetid: 6f3410c4-7944-448f-bae8-bab3e8152d46
caps.latest.revision: "34"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 6aefdb5ecbc8db1470c4297a10d878763c7974de
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="search-a-report-using-url-access"></a>Поиск отчета с использованием URL-адресов
  URL-адрес можно использовать для поиска в отчете определенного текста. Для поиска в отчете задайте в качестве значения параметра *rc:FindString* в URL-адресе текст, который необходимо найти. Можно также использовать параметры *rc:StartFind* и *rc:EndFind* , чтобы сузить поиск определенными страницами внутри отчета.  
  
## <a name="example"></a>Пример  
 В следующем примере выполняется поиск первого упоминания текста «Mountain-400» в образце отчета «Каталог продукции», начиная с первой страницы и заканчивая пятой:  
  
```  
http://server/Reportserver?/SampleReports/Product Catalog&rs:Command=Render&rc:StartFind=1&rc:EndFind=5&rc:FindString=Mountain-400  
```  
  
## <a name="see-also"></a>См. также раздел  
 [Доступ по URL-адресу (службы SSRS)](../reporting-services/url-access-ssrs.md)   
 [Ссылка на параметр доступа по URL-адресу](../reporting-services/url-access-parameter-reference.md)  
  
  
