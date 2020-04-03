---
title: Пропуск значений для необязательных объектов веб-службы | Документы Майкрософт
description: Некоторые свойства сложных типов веб-служб сервера отчетов поддерживают указанное свойство, которое позволяет опустить значение для некоторых записываемых свойств.
ms.date: 03/04/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server-web-service
ms.topic: reference
helpviewer_keywords:
- Web service [Reporting Services], omitted values
- XML Web service [Reporting Services], omitted values
- Report Server Web service, omitted values
- omitting values [Reporting Services]
ms.assetid: ceb68b8b-9214-4745-abc9-f47f33ecd6f7
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 3a7ea9c535092201eaa2c901ef11975bf1461d52
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "79509675"
---
# <a name="omitting-values-for-optional-web-service-objects"></a>Пропуск значений для необязательных объектов веб-службы
  Свойства некоторых сложных типов веб-служб сервера отчетов имеют сопутствующее свойство, известное как свойство Specified. Имя этого свойства состоит из исходного имени свойства и присоединенного к нему слова «Specified». Наличие этого свойства указывает на то, что значение исходного свойства может быть пропущено. Это прямой результат перевода с языка описания веб-служб (WSDL) в класс-посредник платформы [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. Например, свойство веб-службы <xref:ReportService2010.DataSourceDefinition.Enabled%2A> сложного типа <xref:ReportService2010.DataSourceDefinition> имеет сопутствующее свойство с именем <xref:ReportService2010.DataSourceDefinition.EnabledSpecified%2A>. Если при сборке приложения нежелательно задавать значение свойства <xref:ReportService2010.DataSourceDefinition.Enabled%2A>, то не нужно указывать значение для <xref:ReportService2010.DataSourceDefinition.Enabled%2A>. Будет использоваться значение по умолчанию **true**. Однако все же нужно установить для свойства <xref:ReportService2010.DataSourceDefinition.EnabledSpecified%2A> значение **false**. Если для свойства <xref:ReportService2010.DataSourceDefinition.Enabled%2A> задается значение, необходимо задать для свойства <xref:ReportService2010.DataSourceDefinition.EnabledSpecified%2A> значение, равное **true**. Это касается свойств, доступных для записи. Для свойств, доступных только для чтения, не требуется предпринимать каких-либо действий.  
  
> [!IMPORTANT]  
>  Ошибка в указании свойства с помощью вышеприведенной методики может привести к непредсказуемому поведению веб-службы.  
  
 Типы данных, обычно требующие обработки дополнительного свойства Specified: **Boolean**, **DateTime** и **Enumeration**.  
  
 Пример см. в описании метода <xref:ReportService2010.ReportingService2010.CreateDataSource%2A>.  
  
## <a name="see-also"></a>См. также:  
 [Создание приложений с помощью веб-службы и .NET Framework](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Технический справочник (службы SSRS)](../../../reporting-services/technical-reference-ssrs.md)  
  
  
