---
title: Класс событий Lock:Acquired | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Acquired event class
ms.assetid: a6b1df2a-06ed-4fc3-8a84-f0becd5810d5
caps.latest.revision: 37
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 5f3e517a4bc6713834d76a5eade2b67ef1f6ded0
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2018
---
# <a name="lockacquired-event-class"></a>Класс событий Lock:Acquired
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Класс событий Lock:Acquired указывает, что была получена блокировка для ресурса, например страницы данных.  
  
 Классы событий Lock:Acquired и Lock:Released можно применять для отслеживания блокировок объектов, типов блокировок и длительности их действия. Следует исследовать причины длительных захватов, так как они могут приводить к конфликтным ситуациям. Например, приложение может получать блокировку строк в таблице и затем ожидать ввода пользователя. Поскольку ввод данных пользователем может занять много времени, блокировка может помешать работать другим пользователям. В данном случае приложение необходимо перестроить таким образом, чтобы запросы на блокировку выполнялись только при необходимости и оно не ожидало ввода данных пользователем после запроса на блокировку.  
  
## <a name="lockacquired-event-class-data-columns"></a>Столбцы данных класса событий Lock:Acquired  
  
|Имя столбца данных|Тип данных|Описание|Идентификатор столбца|Фильтруемый|  
|----------------------|---------------|-----------------|---------------|----------------|  
|ApplicationName|**nvarchar**|Имя клиентского приложения, установившего соединение с экземпляром [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Этот столбец заполняется значениями, передаваемыми приложением, а не отображаемым именем программы.|10|Да|  
|BigintData1|**bigint**|Идентификатор секции, если блокируемый ресурс секционирован.|52|Да|  
|BinaryData|**image**|Идентификатор ресурса блокировки.|2|Да|  
|ClientProcessID|**int**|Идентификатор, присвоенный главным компьютером сервера процессу, в котором работает клиентское приложение. Этот столбец данных заполняется в том случае, если клиент предоставляет идентификатор клиентского процесса.|9|Да|  
|DatabaseID|**int**|Идентификатор базы данных, в которой запрашивается блокировка. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] отображает имя базы данных, если столбец данных ServerName захвачен при трассировке и сервер доступен. Определите значение для базы данных, используя функцию DB_ID.|3|Да|  
|Duration|**bigint**|Длительность (в микросекундах) между выдачей запроса на блокировку и получением блокировки.|13|Да|  
|EndTime|**datetime**|Время окончания события.|15|Да|  
|EventClass|**int**|Тип события = 24.|27|нет|  
|EventSequence|**int**|Последовательность данного события в запросе.|51|нет|  
|GroupID|**int**|Идентификатор группы рабочей нагрузки, в которой запускается событие трассировки SQL.|66|Да|  
|HostName|**nvarchar**|Имя компьютера, на котором выполняется клиентская программа. Этот столбец данных заполняется, если клиент предоставляет имя узла. Чтобы определить имя узла, используйте функцию HOST_NAME.|8|Да|  
|IntegerData2|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|55|Да|  
|IsSystem|**int**|Указывает, произошло событие в системном или в пользовательском процессе. 1 = системный, 0 = пользовательский.|60|Да|  
|LoginName|**nvarchar**|Имя входа пользователя (либо защищенное имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , либо учетные данные входа Windows в формате домен\имя_пользователя).|11|Да|  
|LoginSid|**image**|Идентификатор безопасности вошедшего в систему пользователя. Эти сведения можно найти в представлении каталога sys.server_principals. Значение идентификатора безопасности уникально для каждого имени входа на сервере.|41|Да|  
|Режим|**int**|Результирующий режим после получения блокировки.<br /><br /> 0=NULL — совместим с любыми другими режимами блокировки (LCK_M_NL)<br /><br /> 1 = блокировка стабильности схемы (LCK_M_SCH_S)<br /><br /> 2 = блокировка изменения схемы (LCK_M_SCH_S)<br /><br /> 3 = совмещаемая блокировка (LCK_M_S)<br /><br /> 4 = блокировка обновления (LCK_M_U)<br /><br /> 5 = монопольная блокировка (LCK_M_X)<br /><br /> 6 = коллективная блокировка намерения (LCK_M_IS)<br /><br /> 7 = блокировка намерения обновления (LCK_M_IU)<br /><br /> 8 = монопольная блокировка намерения (LCK_M_IX)<br /><br /> 9 = совмещаемая блокировка с намерением обновления (LCK_M_SIU)<br /><br /> 10 = совмещаемая блокировка с намерением монопольного доступа (LCK_M_SIX)<br /><br /> 11 = блокировка обновления с намерением монопольного доступа (LCK_M_UIX)<br /><br /> 12 = блокировка массового обновления (LCK_M_BU)<br /><br /> 13 = совмещаемая блокировка диапазона ключей — совмещаемая блокировка (LCK_M_RS_S)<br /><br /> 14 = совмещаемая блокировка диапазона ключей — блокировка обновления (LCK_M_RS_U)<br /><br /> 15 = блокировка вставки в диапазон ключей — блокировка NULL (LCK_M_RI_NL)<br /><br /> 16 = блокировка вставки в диапазон ключей — совмещаемая блокировка (LCK_M_RI_S)<br /><br /> 17 = блокировка вставки в диапазон ключей — блокировка обновления (LCK_M_RI_U)<br /><br /> 18 = блокировка вставки в диапазон ключей — монопольная блокировка (LCK_M_RI_X)<br /><br /> 19 = монопольная блокировка диапазона ключей — совмещаемая блокировка (LCK_M_RX_S)<br /><br /> 20 = монопольная блокировка диапазона ключей — блокировка обновления (LCK_M_RX_U)<br /><br /> 21 = монопольная блокировка диапазона ключей — монопольная блокировка (LCK_M_RX_X)|32|Да|  
|NTDomainName|**nvarchar**|Домен Windows, к которому принадлежит пользователь.|7|Да|  
|NTUserName|**nvarchar**|Имя пользователя Windows.|6|Да|  
|ObjectID|**int**|Идентификатор объекта, для которого была получена блокировка, если он существует и доступен.|22|Да|  
|ObjectID2|**bigint**|Идентификатор связанного объекта или сущности, если он доступен и применим.|56|Да|  
|OwnerID|**int**|1 = TRANSACTION<br /><br /> 2 = CURSOR<br /><br /> 3 = SESSION<br /><br /> 4 = SHARED_TRANSACTION_WORKSPACE<br /><br /> 5 = EXCLUSIVE_TRANSACTION_WORKSPACE|58|Да|  
|RequestID|**int**|Идентификатор запроса, содержащего инструкцию.|49|Да|  
|ServerName|**nvarchar**|Имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , для которого производится трассировка.|26|нет|  
|SessionLoginName|**nvarchar**|Имя входа пользователя, создавшего этот сеанс. Например, при соединении с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] под именем Login1 и при выполнении инструкции под именем Login2 SessionLoginName будет содержать значение Login1, а LoginName — значение Login2. В этом столбце отображаются как имена входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , так и имена входа Windows.|64|Да|  
|SPID|**int**|Идентификатор сеанса, в котором произошло событие.|12|Да|  
|StartTime|**datetime**|Время начала события, если оно известно.|14|Да|  
|TextData|**ntext**|Текстовое значение, зависящее от типа запрошенной блокировки. Это то же значение, что и в столбце resource_description в динамическом представлении управления sys.dm_tran_locks.|1|Да|  
|TransactionID|**bigint**|Назначенный системой идентификатор транзакции.|4|Да|  
|Тип|**int**|1 = NULL_RESOURCE<br /><br /> 2 = DATABASE<br /><br /> 3 = FILE<br /><br /> 5 = OBJECT<br /><br /> 6 = PAGE<br /><br /> 7 = KEY<br /><br /> 8 = EXTENT<br /><br /> 9 = RID<br /><br /> 10 = APPLICATION<br /><br /> 11 = METADATA<br /><br /> 12 = AUTONAMEDB<br /><br /> 13 = HOBT<br /><br /> 14 = ALLOCATION_UNIT|57|Да|  
  
## <a name="see-also"></a>См. также:  
 [Класс событий Lock:Released](../../relational-databases/event-classes/lock-released-event-class.md)   
 [Хранимая процедура sp_trace_setevent (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [sys.dm_tran_locks (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-tran-locks-transact-sql.md)  
  
  
