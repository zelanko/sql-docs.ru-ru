---
title: "Поиск отчета с использованием URL-адресов | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "поиск в отчетах"
  - "поиски текста [службы Reporting Services]"
  - "доступ по URL-адресу [службы Reporting Services], операции поиска в отчете"
ms.assetid: 6f3410c4-7944-448f-bae8-bab3e8152d46
caps.latest.revision: 34
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 34
---
# Поиск отчета с использованием URL-адресов
  URL-адрес можно использовать для поиска в отчете определенного текста. Для поиска в отчете задайте в качестве значения параметра *rc:FindString* в URL-адресе текст, который необходимо найти. Можно также использовать параметры *rc:StartFind* и *rc:EndFind* , чтобы сузить поиск определенными страницами внутри отчета.  
  
## Пример  
 В следующем примере выполняется поиск первого упоминания текста «Mountain-400» в образце отчета «Каталог продукции», начиная с первой страницы и заканчивая пятой:  
  
```  
http://server/Reportserver?/SampleReports/Product Catalog&rs:Command=Render&rc:StartFind=1&rc:EndFind=5&rc:FindString=Mountain-400  
```  
  
## См. также раздел  
 [Доступ по URL-адресу (службы SSRS)](../reporting-services/url-access-ssrs.md)   
 [Ссылка на параметр доступа по URL-адресу](../reporting-services/url-access-parameter-reference.md)  
  
  