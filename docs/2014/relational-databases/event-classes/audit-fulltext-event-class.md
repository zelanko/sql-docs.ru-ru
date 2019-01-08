---
title: Класс событий Audit Fulltext | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
ms.assetid: 95e4c5fd-e16f-446e-b42b-105495a8f39a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1ad7019b30555077d274af62156115cfb71944fc
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52816276"
---
# <a name="audit-fulltext-event-class"></a>Класс событий Audit Fulltext
  Класс событий **Аудит полнотекстового поиска** возникает, когда [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] подключается к процессу управляющей программы полнотекстовой фильтрации и взаимодействует с ней.  
  
## <a name="audit-fulltext-event-class-data-columns"></a>Столбцы данных класса событий Audit Fulltext  
  
|Имя столбца данных|Тип данных|Описание|Идентификатор столбца|Фильтруемый|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**Ошибка**|**int**|Код ошибки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , если событие сигнализирует об ошибке.|31|Да|  
|**EventSequence**|**int**|Порядковый номер данного события в запросе.|51|Нет|  
|**EventSubClass**|**int**|Тип соединения, используемого для входа. 1 = без пула, 2 = в пуле.|21|Да|  
|**IsSystem**|**int**|Указывает, произошло событие в системном или в пользовательском процессе. 1 = системный, 0 = пользовательский.|60|Да|  
|**SessionLoginName**|**nvarchar**|Имя входа пользователя, создавшего этот сеанс. Например, при подключении к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] по имени Имя_входа1 и при выполнении инструкции под именем Имя_входа2 **SessionLoginName** содержит значение «Имя_входа1», а **LoginName** содержит значение «Имя_входа2». В этом столбце отображаются как имена входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , так и имена входа Windows.|64|Да|  
|**SPID**|**int**|Идентификатор сеанса, в котором произошло событие.|12|Да|  
|**StartTime**|**datetime**|Время начала события, если оно известно.|14|Да|  
|**Успешно**|**int**|1 = успешное завершение. 0 = неуспешное завершение. Например, значение 1 означает успешную проверку разрешений, а значение 0 означает, что эта проверка не пройдена.|23|Да|  
|**TargetLoginName**|**int**|Для действий с именем входа (таких как добавление нового имени входа) — имя входа, с которым совершается действие.|42|Да|  
|**TargetLoginSid**|**int**|Для действий с именем входа (таких как добавление нового имени входа) — идентификатор безопасности имени входа, с которым совершается действие.|43|Да|  
|**TextData**|**ntext**|Текстовая информация о событии полнотекстового индекса. Обычно это поле предоставляет информацию о соединении между процессом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и процессом управляющей программы полнотекстовой фильтрации|1|Да|  
  
## <a name="see-also"></a>См. также  
 [Расширенные события](../extended-events/extended-events.md)   
 [Хранимая процедура sp_trace_setevent (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  
