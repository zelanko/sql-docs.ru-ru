---
title: Класс событий FT:Crawl Aborted | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- Crawl Aborted event class
ms.assetid: eead8ea6-5051-4689-ab30-4dfbfda01fb9
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 45b8532a83614fa8b45ccff4af8452c3ff36cf79
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85642208"
---
# <a name="ftcrawl-aborted-event-class"></a>Класс событий FT:Crawl Aborted
[!INCLUDE [SQL Server - ASDB](../../includes/applies-to-version/sql-asdb.md)]
  События класса **FT:Crawl Aborted** указывают на то, что при выполнении полнотекстового сканирования произошло исключение. Данная ошибка обычно приводит к остановке полнотекстового сканирования. Проверьте журнал сканирования и журнал событий [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows на предмет дополнительных сведений об ошибках.  
  
## <a name="ftcrawl-aborted-event-class-data-columns"></a>Столбцы данных класса событий FT:Crawl Aborted  
  
|Имя столбца данных|Тип данных|Description|Идентификатор столбца|Фильтруемый|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**DatabaseID**|**int**|Идентификатор базы данных, в которой выполняется полнотекстовое сканирование. Определите значение для базы данных, используя функцию DB_ID.|3|Да|  
|**Ошибка**|**int**|Номер ошибки для данного события. Часто это номер ошибки, хранимый в таблице **sysmessages** .|31|Да|  
|**EventClass**|**int**|Тип события = 157.|27|нет|  
|**EventSequence**|**int**|Последовательность данного события в запросе.|51|нет|  
|**IsSystem**|**int**|Указывает, произошло событие в системном или в пользовательском процессе. 1 = системный, 0 = пользовательский.|60|Да|  
|**ObjectID**|**int**|Назначенный системой идентификатор объекта, при полнотекстовом сканировании которого произошла ошибка.|22|Да|  
|**SessionLoginName**|**nvarchar**|Имя входа пользователя, создавшего этот сеанс. Например, при подключении к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] по имени "Имя_входа1" и при выполнении инструкции под именем "Имя_входа2" **SessionLoginName** содержит значение "Имя_входа1", а **LoginName** — значение "Имя_входа2". В этом столбце отображаются как имена входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , так и имена входа Windows.|64|Да|  
|**SPID**|**int**|Идентификатор сеанса, в котором произошло событие.|12|Да|  
|**StartTime**|**datetime**|Время начала события, если оно известно.|14|Да|  
|**Состояние**|**int**|Эквивалентно коду состояния ошибки.|30|Да|  
|**TransactionID**|**bigint**|Назначенный системой идентификатор транзакции.|4|Да|  
  
## <a name="see-also"></a>См. также:  
 [Хранимая процедура sp_trace_setevent (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)  
  
  
