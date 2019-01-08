---
title: Основные сведения о поставщике WMI для событий сервера | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- architecture [WMI]
- SQL Server Agent [WMI]
- WMI Provider for Server Events, about WMI Provider for Server Events
ms.assetid: 8fd7bd18-76d0-4b28-8fee-8ad861441ab2
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 2deedb64e5c8995524978a19b02110a068bde08d
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/13/2018
ms.locfileid: "53358216"
---
# <a name="understanding-the-wmi-provider-for-server-events"></a>Основные сведения о поставщике WMI для событий сервера
  Поставщик инструментария WMI для событий сервера позволяет использовать Инструментарий управления Windows (WMI) для контроля событий в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. В ходе своей работы поставщик преобразует [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в управляемый объект инструментария WMI. Этот поставщик позволяет инструментарию WMI использовать все события, которые могут формировать уведомления о событии в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Кроме того, агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], играя роль управляющего приложения, взаимодействующего с инструментарием WMI, может реагировать на эти события, расширяя область событий, охватываемых агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предыдущих версий.  
  
 Управляющие приложения, такие как агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], могут получать доступ к событиям [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью поставщика WMI для событий сервера путем выполнения инструкций WMI Query Language (WQL). WQL является упрощенным подмножеством языка SQL с некоторыми расширениями, специфичными для WMI. При использовании языка WQL приложение получает тип события для определенной базы данных или объекта базы данных. Поставщик WMI для событий сервера преобразовывает запрос в уведомление о событии, создавая уведомление в базе данных-получателе. Дополнительные сведения о работе уведомлений о событиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в разделе [поставщик WMI для событий сервера основные понятия](https://technet.microsoft.com/library/ms180560.aspx). События, которые можно запросить, перечислены в [поставщик WMI для событий классов и свойств сервера](../../relational-databases/wmi-provider-server-events/wmi-provider-for-server-events-classes-and-properties.md).  
  
 При возникновении события, которое вызывает уведомление о событии для отправки сообщения, сообщение направляется в стандартную целевую службу в **msdb** с именем **SQL/Notifications/ProcessWMIEventProviderNotification/v1.0**. Служба ставит событие в стандартную очередь в **msdb** с именем **WMIEventProviderNotificationQueue**. (Служба и очередь создаются динамически при первом подключении поставщика к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].) Затем поставщик считывает сведения о событии из этой очереди и преобразует их в формат управляющих объектов (MOF), прежде чем возвращать их приложению. На следующем рисунке показан этот процесс.  
  
 ![Схема потока поставщик WMI для событий сервера](../../../2014/database-engine/dev-guide/media/wmi-provider-functional-spec.gif "схема потока поставщик WMI для событий сервера")  
  
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
  
 В этом примере `SQLWEP_76CF38C1_18BB_42DD_A7DC_C8820155B0E9` представляет собой идентификатор [!INCLUDE[tsql](../../includes/tsql-md.md)], составленный из префикса `SQLWEP_` и GUID. `SQLWEP` создает новый идентификатор GUID для каждого идентификатора. Значение `A7E5521A-1CA6-4741-865D-826F804E5135` в `TO SERVICE` предложение — это GUID, определяющий экземпляр брокера в **msdb** базы данных.  
  
 Дополнительные сведения о работе с WQL см. в разделе [использование WQL с поставщиком WMI для событий сервера](https://technet.microsoft.com/library/ms180524\(v=sql.105\).aspx).  
  
 Приложения для управления направляют поставщик WMI для событий сервера на экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] путем соединения с пространством имен WMI, определенном поставщиком. Служба Windows WMI сопоставляет это пространство имен с файлом поставщика Sqlwep.dll и загружает его в память. Поставщик управляет пространством имен WMI для событий сервера для каждого экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], а формат: \\ \\.\\ *корневой*\Microsoft\SqlServer\ServerEvents\\*имя_экземпляра*, где *имя_экземпляра* по умолчанию равно MSSQLSERVER. Дополнительные сведения о том, как подключиться к пространству имен WMI для экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в разделе [использование WQL с поставщиком WMI для событий сервера](https://technet.microsoft.com/library/ms180524\(v=sql.105\).aspx).  
  
 Библиотека поставщика Sqlwep.dll загружается в службу WMI в операционной системе сервера только один раз независимо от количества экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], находящихся на сервере.  
  
 Пример [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] приложения агента управления, использующего поставщик WMI для событий сервера, см. в разделе [пример: Создание предупреждения агента SQL Server, с помощью поставщика WMI для событий сервера](https://technet.microsoft.com/library/ms186385.aspx). Пример приложения для управления, использующего поставщик WMI для событий сервера в управляемом коде, см. в разделе [пример: Использование поставщика событий WMI в управляемом коде](https://technet.microsoft.com/library/ms179315.aspx). Дополнительные сведения можно также получить о WMI в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK.  
  
## <a name="see-also"></a>См. также  
 [Основные понятия о поставщике WMI для событий сервера](https://technet.microsoft.com/library/ms180560.aspx)  
  
  
