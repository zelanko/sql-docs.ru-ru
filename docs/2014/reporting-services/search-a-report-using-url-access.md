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
ms.topic: article
helpviewer_keywords:
- searching reports
- text searches [Reporting Services]
- URL access [Reporting Services], report searches
ms.assetid: 6f3410c4-7944-448f-bae8-bab3e8152d46
caps.latest.revision: 34
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: 95989e61ed3b5d77e6896ae9896b1db495ff0a32
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36096069"
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
  
  