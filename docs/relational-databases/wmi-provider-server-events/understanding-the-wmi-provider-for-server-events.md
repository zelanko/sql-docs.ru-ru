---
title: Основные сведения о поставщике WMI для событий сервера
description: Узнайте, как поставщик WMI для событий сервера использует инструментарий управления Windows (WMI) для мониторинга событий, переключив SQL Server в управляемый объект WMI.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- architecture [WMI]
- SQL Server Agent [WMI]
- WMI Provider for Server Events, about WMI Provider for Server Events
ms.assetid: 8fd7bd18-76d0-4b28-8fee-8ad861441ab2
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 6187c97f246a8c4eb445fb0afe224922b2c57f03
ms.sourcegitcommit: 783b35f6478006d654491cb52f6edf108acf2482
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/09/2020
ms.locfileid: "91891964"
---
# <a name="understanding-the-wmi-provider-for-server-events"></a>Основные сведения о поставщике WMI для событий сервера
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Поставщик инструментария WMI для событий сервера позволяет использовать Инструментарий управления Windows (WMI) для контроля событий в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. В ходе своей работы поставщик преобразует [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в управляемый объект инструментария WMI. Этот поставщик позволяет инструментарию WMI использовать все события, которые могут формировать уведомления о событии в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Кроме того, агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], играя роль управляющего приложения, взаимодействующего с инструментарием WMI, может реагировать на эти события, расширяя область событий, охватываемых агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предыдущих версий.  
  
 Управляющие приложения, такие как агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], могут получать доступ к событиям [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью поставщика WMI для событий сервера путем выполнения инструкций WMI Query Language (WQL). WQL является упрощенным подмножеством языка SQL с некоторыми расширениями, специфичными для WMI. При использовании языка WQL приложение получает тип события для определенной базы данных или объекта базы данных. Поставщик WMI для событий сервера преобразовывает запрос в уведомление о событии, создавая уведомление в базе данных-получателе. Дополнительные сведения о работе с уведомлениями о событиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в разделе [Основные понятия поставщика WMI для событий сервера](./wmi-provider-for-server-events-concepts.md). События, которые могут быть запрошены, перечислены в [поставщике WMI для классов и свойств событий сервера](../../relational-databases/wmi-provider-server-events/wmi-provider-for-server-events-classes-and-properties.md).  
  
 Когда возникает событие, запускающее уведомление о событии для отправки сообщения, оно переходит к предопределенной целевой службе в **базе данных msdb** с именем **SQL/Notifications/ProcessWMIEventProviderNotification/v 1.0**. Служба помещает событие в предопределенную очередь в **базе данных msdb** с именем **WMIEventProviderNotificationQueue**. (Служба и очередь создаются динамически поставщиком при первом соединении с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .) Затем поставщик считывает данные о событиях из этой очереди и преобразует их в формат управляемых объектов (MOF) перед возвратом в приложение. Данный процесс показан на следующем рисунке.  
  
 ![Блок-схема поставщика WMI для событий сервера](../../relational-databases/wmi-provider-server-events/media/wmi-provider-functional-spec.gif "Блок-схема поставщика WMI для событий сервера")  
  
 Например, рассмотрим следующий WQL-запрос.  
  
```  
SELECT * FROM DDL_DATABASE_LEVEL_EVENTS  
WHERE DatabaseName = 'AdventureWorks'  
```  
  
 В ответе на этот запрос поставщик WMI для событий сервера создает соответствующее уведомление о событии в базе данных-получателе:  
  
```  
USE AdventureWorks ;  
GO  
CREATE EVENT NOTIFICATION SQLWEP_76CF38C1_18BB_42DD_A7DC_C8820155B0E9  
    ON DATABASE  
    WITH FAN_IN  
    FOR DDL_DATABASE_LEVEL_EVENTS  
    TO SERVICE  
        'SQL/Notifications/ProcessWMIEventProviderNotification/v1.0',   
        'A7E5521A-1CA6-4741-865D-826F804E5135';  
GO  
```  
  
 В этом примере `SQLWEP_76CF38C1_18BB_42DD_A7DC_C8820155B0E9` представляет собой идентификатор [!INCLUDE[tsql](../../includes/tsql-md.md)], составленный из префикса `SQLWEP_` и GUID. `SQLWEP` создает новый идентификатор GUID для каждого идентификатора. Значение `A7E5521A-1CA6-4741-865D-826F804E5135` в `TO SERVICE` предложении является идентификатором GUID, идентифицирующим экземпляр брокера в базе данных **msdb** .  
  
 Дополнительные сведения о работе с WQL см. в разделе [Использование WQL с поставщиком WMI для событий сервера](https://technet.microsoft.com/library/ms180524\(v=sql.105\).aspx).  
  
 Приложения для управления направляют поставщик WMI для событий сервера на экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] путем соединения с пространством имен WMI, определенном поставщиком. Служба Windows WMI сопоставляет это пространство имен с файлом поставщика Sqlwep.dll и загружает его в память. Поставщик управляет пространством имен WMI для событий сервера для каждого экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , а формат: \\ \\ . \\ *root*\микрософт\склсервер\серверевентс \\ *instance_name*, где *INSTANCE_NAME* по умолчанию имеет значение MSSQLSERVER. Дополнительные сведения о подключении к пространству имен WMI для экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в разделе [Использование WQL с поставщиком WMI для событий сервера](https://technet.microsoft.com/library/ms180524\(v=sql.105\).aspx).  
  
 Библиотека поставщика Sqlwep.dll загружается в службу WMI в операционной системе сервера только один раз независимо от количества экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], находящихся на сервере.  
  
 Пример [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] приложения управления агентом, использующего поставщик WMI для событий сервера, см. в разделе [Sample: создание агент SQL Server предупреждения с помощью поставщика WMI для событий сервера](./sample-creating-a-sql-server-agent-alert-with-the-wmi-provider.md). Пример приложения управления, использующего поставщик WMI для событий сервера в управляемом коде, см. в разделе [пример. Использование поставщика событий WMI в управляемом коде](./sample-using-the-wmi-event-provider-with-the-net-framework.md). Дополнительные сведения также доступны в пакете SDK для WMI [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] .  
  
## <a name="see-also"></a>См. также:  
 [Основные понятия о поставщике WMI для событий сервера](./wmi-provider-for-server-events-concepts.md)  
  
