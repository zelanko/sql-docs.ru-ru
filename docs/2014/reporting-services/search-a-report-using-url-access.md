---
title: Поиск отчета с использованием URL-адресов | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- searching reports
- text searches [Reporting Services]
- URL access [Reporting Services], report searches
ms.assetid: 6f3410c4-7944-448f-bae8-bab3e8152d46
caps.latest.revision: 34
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 045c7b045048e625985e17d4a3bf836926bc1fc4
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37230194"
---
# <a name="search-a-report-using-url-access"></a>Поиск отчета с использованием URL-адресов
  URL-адрес можно использовать для поиска в отчете определенного текста. Для поиска в отчете задайте в качестве значения параметра *rc:FindString* в URL-адресе текст, который необходимо найти. Можно также использовать параметры *rc:StartFind* и *rc:EndFind* , чтобы сузить поиск определенными страницами внутри отчета.  
  
## <a name="example"></a>Пример  
 В следующем примере выполняется поиск первого упоминания текста «Mountain-400» в образце отчета «Каталог продукции», начиная с первой страницы и заканчивая пятой:  
  
```  
http://server/Reportserver?/SampleReports/Product Catalog&rs:Command=Render&rc:StartFind=1&rc:EndFind=5&rc:FindString=Mountain-400  
```  
  
## <a name="see-also"></a>См. также  
 [URL-адресов &#40;SSRS&#41;](url-access-ssrs.md)   
 [Ссылка на параметр доступа по URL-адресу](url-access-parameter-reference.md)  
  
  
