---
title: 'Progress Report: Online Index Operation | Документация Майкрософт'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- 'Progress Report: Online Index Operation event class [SQL Server]'
ms.assetid: 491616c1-f666-4b16-a5ea-1192bf156692
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3d0efc3d22fcba588c1104d716cbab0f26eff374
ms.sourcegitcommit: 495913aff230b504acd7477a1a07488338e779c6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/06/2019
ms.locfileid: "68811260"
---
# <a name="progress-report-online-index-operation-event-class"></a>Progress Report: класс события Online Index Operation
  Класс событий Progress Report: Online Index Operation указывает ход операции оперативного построения индекса.  
  
## <a name="progress-report-online-index-operation-event-class-data-columns"></a>Progress Report: Online Index Operation  
  
|Имя столбца данных|Тип данных|Описание|Идентификатор столбца|Фильтруемый|  
|----------------------|---------------|-----------------|---------------|----------------|  
|ApplicationName|`nvarchar`|Имя клиентского приложения, установившего соединение с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Этот столбец заполняется значениями, передаваемыми приложением, а не отображаемым именем программы.|10|Да|  
|BigintData1|`bigint`|Количество вставленных строк.|52|Да|  
|BigintData2|`bigint`|0 = последовательный план, в противном случае — идентификатор потока при параллельном выполнении.|53|Да|  
|ClientProcessID|`int`|Идентификатор, присвоенный главным компьютером сервера процессу, в котором работает клиентское приложение. Этот столбец данных заполняется в том случае, если клиент предоставляет идентификатор клиентского процесса.|9|Да|  
|DatabaseID|`int`|Идентификатор базы данных, указанной в инструкции USE *database* , или базы данных по умолчанию, если для данного экземпляра инструкция USE *database* не выполнялась. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] отображает имя базы данных, если столбец данных ServerName захвачен при трассировке и сервер доступен. Определите значение для базы данных, используя функцию DB_ID.|3|Да|  
|DatabaseName|`nvarchar`|Имя базы данных, в которой выполняется пользовательская инструкция.|35|Да|  
|Duration|`bigint`|Длительность события (в микросекундах).|13|Да|  
|EndTime|`datetime`|Время завершения операции с индексами в сети.|15|Да|  
|EventClass|`int`|Тип события = 190.|27|Нет|  
|EventSequence|`int`|Последовательность данного события в запросе.|51|Нет|  
|EventSubClass|`int`|Тип подкласса события.<br /><br /> 1 = начало<br /><br /> 2 = начало выполнения этапа 1<br /><br /> 3 = этап 1. Выполнение закончилось<br /><br /> 2 = этап 2. Выполнение началось<br /><br /> 3 = этап 2. Выполнение закончилось<br /><br /> 6 = счетчик вставленных строк<br /><br /> 7 = готово<br /><br /> Этап 1 относится к базовому объекту (кластеризованному индексу или куче) или если операция с индексами включает только один некластеризованный индекс. Этап 2 используется, когда операция построения индекса включает исходное перестроение и дополнительные некластеризованные индексы.  Например, если у объекта есть кластеризованный индекс и несколько некластеризованных индексов, то "Rebuild ALL" перестроит все индексы. Базовый объект (кластеризованный индекс) перестраивается на этапе 1, а затем все некластеризованные индексы перестраиваются на этапе 2.|21|Да|  
|GroupID|`int`|Идентификатор группы рабочей нагрузки, в которой запускается событие трассировки SQL.|66|Да|  
|HostName|`nvarchar`|Имя компьютера, на котором выполняется клиентская программа. Этот столбец данных заполняется, если клиент предоставляет имя узла. Чтобы определить имя узла, используйте функцию HOST_NAME.|8|Да|  
|IndexID|`int`|Идентификатор индекса объекта, связанного с событием.|24|Да|  
|IsSystem|`int`|Указывает, произошло событие в системном или в пользовательском процессе. 1 = системный, 0 = пользовательский.|60|Да|  
|LoginName|`nvarchar`|Имя входа пользователя (либо защищенное имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , либо учетные данные входа [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows в формате «ДОМЕН\имя_пользователя»).|11|Да|  
|LoginSid|`image`|Идентификатор безопасности вошедшего в систему пользователя. Эти сведения можно найти в представлении каталога sys.server_principals. Значение идентификатора безопасности уникально для каждого имени входа на сервере.|41|Да|  
|NTDomainName|`nvarchar`|Домен Windows, к которому принадлежит пользователь.|7|Да|  
|NTUserName|`nvarchar`|Имя пользователя Windows.|6|Да|  
|ObjectID|`int`|Идентификатор объекта, назначенный системой.|22|Да|  
|ObjectName|`nvarchar`|Имя объекта, на который указывает ссылка.|34|Да|  
|PartitionId|`bigint`|ID формируемой секции.|65|Да|  
|PartitionNumber|`int`|Порядковый номер формируемой секции.|25|Да|  
|ServerName|`nvarchar`|Имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , для которого производится трассировка.|26|Нет|  
|SessionLoginName|`nvarchar`|Имя входа пользователя, создавшего этот сеанс. Например, при соединении с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] под именем Login1 и при выполнении инструкции под именем Login2 SessionLoginName будет содержать значение Login1, а LoginName — значение Login2. В этом столбце отображаются как имена входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , так и имена входа Windows.|64|Да|  
|SPID|`int`|Идентификатор сеанса, в котором произошло событие.|12|Да|  
|StartTime|`datetime`|Время начала события.|14|Да|  
|TransactionID|`bigint`|Назначенный системой идентификатор транзакции.|4|Да|  
  
## <a name="see-also"></a>См. также  
 [Хранимая процедура sp_trace_setevent (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  
