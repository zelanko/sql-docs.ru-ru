---
title: Класс событий Lock:Deadlock Chain | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
topic_type:
- apiref
helpviewer_keywords:
- Deadlock Chain event class
ms.assetid: 9883127b-aa34-4235-88cc-c161cd2112cc
caps.latest.revision: 35
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: df26234f362663fac9d77d9162aedeb70378a2ef
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36097772"
---
# <a name="lockdeadlock-chain-event-class"></a>Класс событий Lock:Deadlock Chain
  Класс событий Lock:Deadlock Chain создается для каждого элемента взаимоблокировки.  
  
 Используйте класс событий Lock:Deadlock Chain для регистрации условий возникновения взаимоблокировок. Эти сведения помогают определить, насколько сильно взаимоблокировки влияют на производительность приложения и какие объекты при этом задействованы. Чтобы определить, можно ли свести к минимуму вероятность взаимоблокировок, проанализируйте в своем приложении код, изменяющий эти объекты.  
  
## <a name="lockdeadlock-chain-event-class-data-columns"></a>Столбцы класса событий Lock:Deadlock Chain  
  
|Имя столбца данных|Тип данных|Описание|Идентификатор столбца|Фильтруемый|  
|----------------------|---------------|-----------------|---------------|----------------|  
|BinaryData|`image`|Идентификатор ресурса блокировки.|2|Да|  
|DatabaseID|`int`|Идентификатор базы данных, к которой относится ресурс. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] отображает имя базы данных, если столбец данных ServerName захвачен при трассировке и сервер доступен. Определите значение для базы данных, используя функцию DB_ID.|3|Да|  
|DatabaseName|`nvarchar`|Имя базы данных, к которой относится ресурс.|35|Да|  
|EventClass|`int`|Тип события = 59.|27|Нет|  
|EventSequence|`int`|Последовательность данного события в запросе.|51|Нет|  
|EventSubClass|`int`|Тип подкласса события.<br /><br /> 101 = блокировка типа ресурса<br /><br /> 102 = обмен типа ресурса|21|Да|  
|IntegerData|`int`|Номер взаимоблокировки. Отсчет номеров, назначаемых взаимоблокировкам, начинается с нуля при запуске сервера; каждая новая взаимоблокировка получает больший на единицу номер.|25|Да|  
|IntegerData2|`int`|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|55|Да|  
|IsSystem|`int`|Указывает, произошло событие в системном или в пользовательском процессе. 1 = системный, 0 = пользовательский.|60|Да|  
|LoginSid|`image`|Идентификатор безопасности вошедшего в систему пользователя. Эти сведения можно найти в представлении каталога sys.server_principals. Значение идентификатора безопасности уникально для каждого имени входа на сервере.|41|Да|  
|Режим|`int`|0=NULL — совместим с любыми другими режимами блокировки (LCK_M_NL)<br /><br /> 1 = блокировка стабильности схемы (LCK_M_SCH_S)<br /><br /> 2 = блокировка изменения схемы (LCK_M_SCH_S)<br /><br /> 3 = совмещаемая блокировка (LCK_M_S)<br /><br /> 4 = блокировка обновления (LCK_M_U)<br /><br /> 5 = монопольная блокировка (LCK_M_X)<br /><br /> 6 = коллективная блокировка намерения (LCK_M_IS)<br /><br /> 7 = блокировка намерения обновления (LCK_M_IU)<br /><br /> 8 = монопольная блокировка намерения (LCK_M_IX)<br /><br /> 9 = совмещаемая блокировка с намерением обновления (LCK_M_SIU)<br /><br /> 10 = совмещаемая блокировка с намерением монопольного доступа (LCK_M_SIX)<br /><br /> 11 = блокировка обновления с намерением монопольного доступа (LCK_M_UIX)<br /><br /> 12 = блокировка массового обновления (LCK_M_BU)<br /><br /> 13 = совмещаемая блокировка диапазона ключей — совмещаемая блокировка (LCK_M_RS_S)<br /><br /> 14 = совмещаемая блокировка диапазона ключей — блокировка обновления (LCK_M_RS_U)<br /><br /> 15 = блокировка вставки в диапазон ключей — блокировка NULL (LCK_M_RI_NL)<br /><br /> 16 = блокировка вставки в диапазон ключей — совмещаемая блокировка (LCK_M_RI_S)<br /><br /> 17 = блокировка вставки в диапазон ключей — блокировка обновления (LCK_M_RI_U)<br /><br /> 18 = блокировка вставки в диапазон ключей — монопольная блокировка (LCK_M_RI_X)<br /><br /> 19 = монопольная блокировка диапазона ключей — совмещаемая блокировка (LCK_M_RX_S)<br /><br /> 20 = монопольная блокировка диапазона ключей — блокировка обновления (LCK_M_RX_U)<br /><br /> 21 = монопольная блокировка диапазона ключей — монопольная блокировка (LCK_M_RX_X)|32|Да|  
|ObjectID|`int`|Идентификатор заблокированного объекта, если он доступен и является применимым.|22|Да|  
|ObjectID2|`bigint`|Идентификатор связанного объекта или сущности, если он доступен и является применимым.|56|Да|  
|OwnerID|`int`|1 = TRANSACTION<br /><br /> 2 = CURSOR<br /><br /> 3 = SESSION<br /><br /> 4 = SHARED_TRANSACTION_WORKSPACE<br /><br /> 5 = EXCLUSIVE_TRANSACTION_WORKSPACE|58|Да|  
|RequestID|`int`|Идентификатор запроса, содержащего инструкцию.|49|Да|  
|ServerName|`nvarchar`|Имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , для которого производится трассировка.|26|Нет|  
|SessionLoginName|`nvarchar`|Имя входа пользователя, создавшего этот сеанс. Например, при соединении с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] под именем Login1 и при выполнении инструкции под именем Login2 SessionLoginName будет содержать значение Login1, а LoginName — значение Login2. В этом столбце отображаются как имена входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , так и имена входа [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.|64|Да|  
|SPID|`int`|Идентификатор сеанса, в котором произошло событие.|12|Да|  
|StartTime|`datetime`|Время начала события, если оно известно.|14|Да|  
|TextData|`ntext`|Текстовое значение, зависящее от типа ресурса.|1|Да|  
|TransactionID|`bigint`|Назначенный системой идентификатор транзакции.|4|Да|  
|Тип|`int`|1 = NULL_RESOURCE<br /><br /> 2 = DATABASE<br /><br /> 3 = FILE<br /><br /> 5 = OBJECT<br /><br /> 6 = PAGE<br /><br /> 7 = KEY<br /><br /> 8 = EXTENT<br /><br /> 9 = RID<br /><br /> 10 = APPLICATION<br /><br /> 11 = METADATA<br /><br /> 12 = AUTONAMEDB<br /><br /> 13 = HOBT<br /><br /> 14 = ALLOCATION_UNIT|57|Да|  
  
## <a name="see-also"></a>См. также  
 [Хранимая процедура sp_trace_setevent (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)   
 [sys.dm_tran_locks (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-tran-locks-transact-sql)  
  
  
