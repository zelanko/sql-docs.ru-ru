---
title: Использование защищенных методов веб-службы | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SOAP [Reporting Services], secure connections
- Web service [Reporting Services], SOAP
- Report Server Web service, SOAP
- XML Web service [Reporting Services], SOAP
ms.assetid: 87329299-c2ea-4517-9148-d855726768a9
caps.latest.revision: 36
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 7e05a1656395828181f8622f82a4127107fa8ecc
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37238324"
---
# <a name="using-secure-web-service-methods"></a>Использование защищенных методов веб-службы
  При вызове некоторых из методов веб-служб сервера отчетов может потребоваться наличие безопасного соединения. То, для каких из методов требуется наличие безопасного соединения, определяется значением параметра `SecureConnectionLevel` в файле RSReportServer.config. Значение этого параметра должно быть целым числом и находиться в диапазоне от 0 и выше. Данные значения описываются в следующей таблице.  
  
|Level|Описание|  
|-----------|-----------------|  
|**0**|Небезопасный. Для вызовов к API SOAP служб Reporting Services не требуется безопасное соединение.|  
|Больше **0**|Безопасный уровень. Для всех вызовов к API-интерфейсу SOAP служб Reporting Services необходимо наличие безопасного соединения.|  
  
 Метод <xref:ReportExecution2005.ReportExecutionService.ListSecureMethods%2A> веб-службы можно использовать для возвращения списка всех методов веб-службы, для которых необходимо наличие безопасного соединения, в соответствии с текущей конфигурацией сервера отчетов. При работе с SSL пользователю необходимо оценить список методов, возвращаемых методом <xref:ReportExecution2005.ReportExecutionService.ListSecureMethods%2A>, и изменить имя схемы URI веб-службы на «https» или «http» в зависимости от вызываемого метода.  
  
## <a name="see-also"></a>См. также  
 [Создание приложений с помощью веб-службы и .NET Framework](building-applications-using-the-web-service-and-the-net-framework.md)   
 [Веб-службы сервера отчетов](../report-server-web-service.md)  
  
  
