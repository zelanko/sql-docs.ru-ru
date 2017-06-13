---
title: "Аргументов метода Web Service | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- Report Server Web service, methods
- Web service [Reporting Services], methods
- methods [Reporting Services], arguments
- XML Web service [Reporting Services], methods
ms.assetid: f7b9ca05-fc4c-4b30-8e5d-172dd0f4a832
caps.latest.revision: 38
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 43fcfe6eecffdc237366eb7963a5582b1915d363
ms.contentlocale: ru-ru
ms.lasthandoff: 06/13/2017

---
# <a name="supplying-web-service-method-arguments"></a>Передача аргументов методу веб-службы
  Метод веб-службы сервера отчетов отправляет запрос в службу по заданному URL-адресу с помощью протокола SOAP по протоколу HTTP. Служба получает запрос, обрабатывает его, а затем возвращает ответное сообщение. Такие запросы и ответы на них имеют форму XML-документов.  
  
## <a name="optional-parameters"></a>Необязательные параметры  
 В некоторых случаях метод веб-службы может иметь необязательные входные параметры. Даже если входной параметр метода веб-службы является необязательным, по-прежнему необходимо включить его и задайте значение параметра **null** (**ничего** в [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]). Установка значения параметра в **null** задает значение элемента для этого параметра в SOAP-запрос **null**.  
  
 В следующем примере используется метод <xref:ReportService2010.ReportingService2010.CreateFolder%2A>, чтобы создать новую папку с именем Product Sales в папке Sales. Указав **null** значения для свойств папки, никакие пользовательские свойства предоставляются для папки:  
  
```  
// C#  
rs.CreateFolder("Product Sales", "/Sales", null);  
```  
  
## <a name="complex-data-types"></a>Сложные типы данных  
 Основным классом веб-службы сервера отчетов является <xref:ReportService2010.ReportingService2010>, который используется для вызова операций SOAP или веб-методов класса-посредника. Чтобы обеспечить поддержку этого класса и его методов, службы [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] включают определяемые пользователем сложные типы данных, относящиеся к входным и выходным параметрам методов веб-службы. Эти сложные типы данных являются частью созданного прокси-класса, который можно использовать при разработке в [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] среды.  
  
 Во время создания класса-посредника сложные типы данных, определенные в WSDL-файле, представляются классами-посредниками, которые включают свойства, соответствующие различным элементам SOAP в сложных типах данных. Последовательности таких типов данных становятся массивами объектов, которые можно перечислять в коде. Это устраняет необходимость непосредственной работы с XML-структурами, отправляемыми в сообщениях SOAP. Платформа [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] выполняет необходимые преобразования.  
  
## <a name="see-also"></a>См. также:  
 [Создание приложений с помощью веб-службы и .NET Framework](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Веб-службы сервера отчетов](../../../reporting-services/report-server-web-service/report-server-web-service.md)   
 [Технический справочник по &#40; Службы SSRS &#41;](../../../reporting-services/technical-reference-ssrs.md)  
  
  
