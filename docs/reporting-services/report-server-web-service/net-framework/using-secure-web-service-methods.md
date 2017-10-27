---
title: "С помощью методов безопасных веб-служб | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
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
- SOAP [Reporting Services], secure connections
- Web service [Reporting Services], SOAP
- Report Server Web service, SOAP
- XML Web service [Reporting Services], SOAP
ms.assetid: 87329299-c2ea-4517-9148-d855726768a9
caps.latest.revision: 36
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: 1222a4223f54eec0f6083790da4d0afebf353ec9
ms.contentlocale: ru-ru
ms.lasthandoff: 08/12/2017

---
# <a name="using-secure-web-service-methods"></a>Использование защищенных методов веб-службы
  При вызове некоторых из методов веб-служб сервера отчетов может потребоваться наличие безопасного соединения. Методы, которые необходимо наличие безопасного соединения определяются **SecureConnectionLevel** в файле RSReportServer.config. Значение этого параметра должно быть целым числом и находиться в диапазоне от 0 и выше. Данные значения описываются в следующей таблице.  
  
|Level|Description|  
|-----------|-----------------|  
|**0**|Небезопасный. Для вызовов к API SOAP служб Reporting Services не требуется безопасное соединение.|  
|Больше, чем **0**|Безопасный уровень. Для всех вызовов к API-интерфейсу SOAP служб Reporting Services необходимо наличие безопасного соединения.|  
  
 Метод <xref:ReportExecution2005.ReportExecutionService.ListSecureMethods%2A> веб-службы можно использовать для возвращения списка всех методов веб-службы, для которых необходимо наличие безопасного соединения, в соответствии с текущей конфигурацией сервера отчетов. При работе с SSL пользователю необходимо оценить список методов, возвращаемых методом <xref:ReportExecution2005.ReportExecutionService.ListSecureMethods%2A>, и изменить имя схемы URI веб-службы на «https» или «http» в зависимости от вызываемого метода.  
  
## <a name="see-also"></a>См. также:  
 [Создание приложений с помощью веб-службы и .NET Framework](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Веб-службы сервера отчетов](../../../reporting-services/report-server-web-service/report-server-web-service.md)  
  
  

