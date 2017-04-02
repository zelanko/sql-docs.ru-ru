---
title: "Новые возможности служб Integration Services в SQL Server&#160;vNext | Microsoft Docs"
ms.custom: ""
ms.date: "03/16/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e26d7884-e772-46fa-bfdc-38567fe976a1
caps.latest.revision: 4
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 3
---
# Новые возможности служб Integration Services в SQL Server&#160;vNext
В этой статье описаны функции, которые были добавлены или обновлены в [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].

>   [!NOTE] В SQL Server vNext также входят функции SQL Server 2016 и функции, добавленные в обновлениях для SQL Server 2016. Сведения о новых возможностях служб SQL Server Integration Services в SQL Server 2016 см. в разделе [Новые возможности служб Integration Services в SQL Server 2016](../integration-services/what-s-new-in-integration-services-in-sql-server-2016.md).

## <a name="new-in-ssis-in-sql-server-vnext-ctp-11"></a>Новые возможности служб SQL Server Integration Services в SQL Server vNext CTP 1.1

В версии SQL Server vNext CTP 1.1 нет новых функций служб SQL Server Integration Services.

## <a name="new-in-ssis-in-sql-server-vnext-ctp-10"></a>Новые возможности служб SQL Server Integration Services в SQL Server vNext CTP 1.0

### <a name="scale-out-for-ssis"></a>Масштабное развертывание для служб SQL Server Integration Services

Функция масштабного развертывания значительно упрощает выполнение [!INCLUDE[ssIS_md](../includes/ssis-md.md)] на нескольких компьютерах. 
   
После установки масштаба главной и рабочих ролей масштабного развертывания пакет можно распространить для автоматического выполнения в различных рабочих ролях. Если происходит непредвиденная остановка выполнения, повторная попытка предпринимается автоматически. Кроме того, всеми выполнениями и рабочими ролями можно централизованно управлять с помощью главной роли.
   
Дополнительные сведения см. в разделе [Масштабное развертывание служб Integration Services](../integration-services/integration-services-ssis-scale-out.md).
   
### <a name="support-for-microsoft-dynamics-online-resources"></a>Поддержка ресурсов Microsoft Dynamics Online

Источник OData и диспетчер подключений OData теперь поддерживают подключение к каналам OData в Microsoft Dynamics AX Online и Microsoft Dynamics CRM Online.
