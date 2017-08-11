---
title: "Пропуск значений для объектов необязательно веб-службы | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
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
- Web service [Reporting Services], omitted values
- XML Web service [Reporting Services], omitted values
- Report Server Web service, omitted values
- omitting values [Reporting Services]
ms.assetid: ceb68b8b-9214-4745-abc9-f47f33ecd6f7
caps.latest.revision: 36
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 727d9ccd8cd1e40d89cfe74291edae92988b407c
ms.openlocfilehash: 3532a470bd036e0128a8df21ca391210cf7209a2
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

---
# <a name="omitting-values-for-optional-web-service-objects"></a>Пропуск значений для необязательных объектов веб-службы
  Свойства некоторых сложных типов службы отчетов имеют сопутствующее свойство, известное как указанное свойство. Имя этого свойства состоит из исходного имени свойства и присоединенного к нему слова «Specified». Наличие этого свойства указывает на то, что значение исходного свойства может быть пропущено. Это прямой результат перевода с языка описания веб-служб (WSDL) в класс-посредник платформы [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. Например, свойство веб-службы <xref:ReportService2010.DataSourceDefinition.Enabled%2A> сложного типа <xref:ReportService2010.DataSourceDefinition> имеет сопутствующее свойство с именем <xref:ReportService2010.DataSourceDefinition.EnabledSpecified%2A>. Если создается приложение и не требуется задать значение для <xref:ReportService2010.DataSourceDefinition.Enabled%2A> свойства, не нужно указывать значение для <xref:ReportService2010.DataSourceDefinition.Enabled%2A>; значение по умолчанию **true** используется. Однако по-прежнему необходимо задать <xref:ReportService2010.DataSourceDefinition.EnabledSpecified%2A> для **false**. Если задать значение для <xref:ReportService2010.DataSourceDefinition.Enabled%2A> свойства, необходимо задать <xref:ReportService2010.DataSourceDefinition.EnabledSpecified%2A> равно **true**. Это касается свойств, доступных для записи. Для свойств, доступных только для чтения, не требуется предпринимать каких-либо действий.  
  
> [!IMPORTANT]  
>  Ошибка в указании свойства с помощью вышеприведенной методики может привести к непредсказуемому поведению веб-службы.  
  
 Типы данных, обычно требующие обработки дополнительного свойства Specified — **логическое**, **DateTime**, и **перечисления**.  
  
 Пример см. в описании метода <xref:ReportService2010.ReportingService2010.CreateDataSource%2A>.  
  
## <a name="see-also"></a>См. также:  
 [Создание приложений с помощью веб-службы и .NET Framework](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Технический справочник по &#40; Службы SSRS &#41;](../../../reporting-services/technical-reference-ssrs.md)  
  
  
