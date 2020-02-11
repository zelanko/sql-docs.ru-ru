---
title: Класс событий Audit Server Operation | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Audit Server Operation event class
ms.assetid: 6cc3dbb9-817e-4329-9f45-c3adcff3b511
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 99f3b353231da86af00bc4531e2645fe0a5b1994
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "63012431"
---
# <a name="audit-server-operation-event-class"></a>Audit Server Operation, класс событий
  Класс событий **Audit Server Operation** возникает при выполнении таких операций аудита безопасности, как настройка параметров, ресурсов, доступа к внешним ресурсам или авторизации.  
  
## <a name="audit-server-operation-event-class-data-columns"></a>Столбцы данных класса событий Audit Server Operation  
  
|Имя столбца данных|Тип данных|Description|Идентификатор столбца|Фильтруемый|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**ApplicationName**|**nvarchar**|Имя клиентского приложения, установившего соединение с экземпляром [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Этот столбец заполняется значениями, передаваемыми приложением, а не отображаемым именем программы.|10|Да|  
|**DatabaseID**|**int**|Идентификатор базы данных, указанной в инструкции USE *database* , или базы данных по умолчанию, если для данного экземпляра инструкция USE *database* не выполнялась. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]Отображает имя базы данных, если столбец данных **ServerName** фиксируется при трассировке и сервер доступен. Определите значение для базы данных, используя функцию DB_ID.|3|Да|  
|**имя_базы_данных**|**nvarchar**|Имя базы данных, в которой выполняется пользовательская инструкция.|35|Да|  
|**дбусернаме**|**nvarchar**|
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|40|Да|  
|**евентсекуенце**|**int**|Последовательность данного события в запросе.|51|нет|  
|**EventSubClass**|**int**|Тип подкласса события.<br /><br /> 1=Administer Bulk Operations<br /><br /> 2=Alter Settings<br /><br /> 3=Alter Resources<br /><br /> 4=Authenticate<br /><br /> 5=External Access<br /><br /> 6=Alter Server State<br /><br /> 7=Unsafe Assembly<br /><br /> 8=Alter Connection<br /><br /> 9=Alter Resource Governor<br /><br /> 10=Use Any Workload Group<br /><br /> 11=View Server State|21|Да|  
|**Имя узла**|**nvarchar**|Имя компьютера, на котором выполняется клиентская программа. Этот столбец данных заполняется, если клиент предоставляет имя узла. Чтобы определить имя узла, используйте функцию HOST_NAME.|8|Да|  
|**Указанным параметром IsSystem**|**int**|Указывает, произошло событие в системном или в пользовательском процессе. 1 = системный, 0 = пользовательский.|60|Да|  
|**LoginName**|**nvarchar**|Имя входа пользователя (либо имя входа безопасности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , либо учетные данные входа [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows в формате «ДОМЕН\имя_пользователя»).|11|Да|  
|**логинсид**|**Эскиз**|Идентификатор безопасности вошедшего в систему пользователя. Эти сведения можно найти в представлении каталога **sys.server_principals** . Значение идентификатора безопасности уникально для каждого имени входа на сервере.|41|Да|  
|**нтдомаиннаме**|**nvarchar**|Домен Windows, к которому принадлежит пользователь.|7|Да|  
|**NTUserName**|**nvarchar**|Имя пользователя Windows.|6|Да|  
|**ИмяОбъекта**|**nvarchar**|Имя объекта, на который указывает ссылка.|34|Да|  
|**ObjectType**|**int**|Значение, представляющее тип объекта, связанного с событием. Это значение соответствует столбцу типа в представлении каталога **sys. Objects** . Значения см. в разделе [Столбец события ObjectType Trace](objecttype-trace-event-column.md).|28|Да|  
|**OwnerName**|**nvarchar**|Имя пользователя базы данных, владеющего объектом.|37|Да|  
|**RequestID**|**int**|Идентификатор запроса, содержащего инструкцию.|49|Да|  
|**Имя**|**nvarchar**|Имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , для которого производится трассировка.|26|нет|  
|**SessionLoginName содержит значение**|**nvarchar**|Имя входа пользователя, создавшего этот сеанс. Например, при подключении к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] по имени "Имя_входа1" и при выполнении инструкции под именем "Имя_входа2" **SessionLoginName** содержит значение "Имя_входа1", а **LoginName** — значение "Имя_входа2". В этом столбце отображаются как имена входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , так и имена входа Windows.|64|Да|  
|**ИНТЕРФЕЙС**|**int**|Идентификатор сеанса, в котором произошло событие.|12|Да|  
|**StartTime**|**datetime**|Время начала события, если оно известно.|14|Да|  
|**Успех**|**int**|1 = успешное завершение. 0 = неуспешное завершение. Например, значение, равное 1, означает успешную проверку разрешений, а значение, равное 0, означает, что эта проверка завершена с ошибкой.|23|Да|  
|**TextData**|**ntext**|Текстовое значение, зависящее от класса событий, фиксируемых при трассировке.|1|Да|  
|**ИД транзакции**|**bigint**|Назначенный системой идентификатор транзакции.|4|Да|  
|**ксактсекуенце**|**bigint**|Токен, используемый для описания текущей транзакции.|50|Да|  
  
## <a name="see-also"></a>См. также:  
 [Расширенные события](../extended-events/extended-events.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  
