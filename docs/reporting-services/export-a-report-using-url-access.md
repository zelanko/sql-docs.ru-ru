---
title: "Экспорт отчета с использованием URL | Документы Microsoft"
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
- formats [Reporting Services], URL rendering
- URL access [Reporting Services], rendering formats
ms.assetid: 6a3b7fc3-3d91-4d12-8371-42ea12e74517
caps.latest.revision: 42
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: d9ee4dd3c00d9e250fd3c773a917ad3cf90f84c4
ms.contentlocale: ru-ru
ms.lasthandoff: 06/13/2017

---
# <a name="export-a-report-using-url-access"></a>Экспорт отчета с применением доступа по URL-адресу
  Можно также указать формат, в котором будет подготовлен отчет, используя параметр URL-адреса *rs:Format* .  Форматы HTML4.0 и HTML5 (модули подготовки отчетов) отображаются прямо в браузере, а для всех остальных форматов браузер предложит сохранить результат в виде локального файла.  
  
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
  
 Если в URL-адрес не включен параметр *Format* , то сервер отчетов определяет браузер и подготавливает для него отчет в соответствующем HTML-формате.  
  
## <a name="see-also"></a>См. также  
 [Доступ по URL-адресу (службы SSRS)](../reporting-services/url-access-ssrs.md)   
 [Ссылка на параметр доступа по URL-адресу](../reporting-services/url-access-parameter-reference.md)  
  
  
