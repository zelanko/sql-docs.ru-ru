---
title: "Экспорт отчета с применением доступа по URL-адресу | Microsoft Docs"
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
  - "форматы [Reporting Services], обработка URL-адресов"
  - "доступ по URL-адресу [Reporting Services], форматы обработки"
ms.assetid: 6a3b7fc3-3d91-4d12-8371-42ea12e74517
caps.latest.revision: 42
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 42
---
# Экспорт отчета с применением доступа по URL-адресу
  Можно также указать формат, в котором будет подготовлен отчет, используя параметр URL-адреса *rs:Format*.  Форматы HTML4.0 и HTML5 (модули подготовки отчетов) отображаются прямо в браузере, а для всех остальных форматов браузер предложит сохранить результат в виде локального файла.  
  
 Например, чтобы получить копию отчета в формате PDF прямо с сервера отчетов, работающего в собственном режиме:  
  
```  
http://myrshost/ReportServer?/myreport&rs:Format=PDF  
```  
  
 И с сервера отчетов, работающего в режиме интеграции с SharePoint:  
  
```  
http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/myrereport.rdl&rs:Format=PDF  
```  
  
 Например, следующая URL-команда в браузере экспортирует отчет из именованного экземпляра сервера отчетов в формат PPTX.  
  
```  
http://servername/ReportServer_THESQLINSTANCE/Pages/ReportViewer.aspx?%2freportfolder%2freport+name+with+spaces&rs:Format=pptx  
```  
  
 Допустимые значения для этого параметра основаны на модулях подготовки отчетов, установленных на сервер отчетов, к которому осуществляется доступ. Поддерживаемые модули: HTML4.0, MHTML, IMAGE, EXCELOPENXML (xlsx), WORDOPENXML (docx), CSV, CSV, PDF, XML и NULL. Если указанный модуль подготовки отчетов не установлен на сервере отчетов, то отчет не будет подготовлен, а браузере выдаст ошибку.  
  
 Если в URL-адрес не включен параметр *Format*, то сервер отчетов определяет браузер и подготавливает для него отчет в соответствующем HTML-формате.  
  
## См. также  
 [Доступ по URL-адресу (службы SSRS)](../reporting-services/url-access-ssrs.md)   
 [Ссылка на параметр доступа по URL-адресу](../reporting-services/url-access-parameter-reference.md)  
  
  