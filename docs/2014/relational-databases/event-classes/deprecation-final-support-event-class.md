---
title: Класс событий Deprecation Final Support | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Deprecation Final Support event class
- deprecation [SQL Server], events final support
ms.assetid: 2b4d88d0-62be-45c0-bea8-c5900d553d31
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f2833f1f342aa212b73611d257b8e29606a14cce
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/25/2020
ms.locfileid: "62662985"
---
# <a name="deprecation-final-support-event-class"></a>класс событий Deprecation Final Support
  Класс событий **Deprecation Final Support** возникает в случае использования функции, которая будет удалена из следующей основной версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Для увеличения срока службы приложения избегайте использования функций, которые приводят к вызову класса событий **Deprecation Final Support** или **Deprecation Announcement** . Модифицируйте приложения, которые используют устаревшие функции, как можно быстрее.  
  
## <a name="deprecation-final-support-event-class-data-columns"></a>Столбцы данных класса событий Deprecation Final Support  
  
|Имя столбца данных|Тип данных|Description|Идентификатор столбца|Фильтруемый|  
|----------------------|---------------|-----------------|---------------|----------------|  
|ApplicationName|`nvarchar`|Имя клиентского приложения, установившего соединение с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Этот столбец заполняется значениями, передаваемыми приложением, а не отображаемым именем программы.|10|Да|  
|ClientProcessID|`int`|Идентификатор, присвоенный главным компьютером сервера процессу, в котором работает клиентское приложение. Этот столбец данных заполняется в том случае, если клиент предоставляет идентификатор клиентского процесса.|9|Да|  
|DatabaseID|`int`|Идентификатор базы данных, указанной в инструкции USE *Database* , или базы данных по умолчанию, если для данного *экземпляра инструкция USE database не* выполнялась. Приложение [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] отображает имя базы данных, если столбец данных `ServerName` захвачен при трассировке и сервер доступен. Определите значение для базы данных, используя функцию DB_ID.|3|Да|  
|имя_базы_данных|`nvarchar`|Имя базы данных, в которой выполняется пользовательская инструкция.|35|Да|  
|EventClass|`int`|Тип события = 126.|27|Нет|  
|EventSequence|`int`|Последовательность данного события в запросе.|51|Нет|  
|HostName|`nvarchar`|Имя компьютера, на котором выполняется клиентская программа. Этот столбец данных заполняется, если клиент предоставляет имя узла. Чтобы определить имя узла, используйте функцию HOST_NAME.|8|Да|  
|IntegerData2|`int`|Смещение конца выполняемой инструкции (в байтах).|55|Да|  
|IsSystem|`int`|Указывает, произошло событие в системном или в пользовательском процессе. 1 = системный, 0 = пользовательский.|60|Да|  
|LoginName|`nvarchar`|Имя входа пользователя (либо защищенное имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , либо учетные данные входа [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows в формате «ДОМЕН\имя_пользователя»).|11|Да|  
|LoginSid|`image`|Идентификатор безопасности вошедшего в систему пользователя. Эти сведения можно найти в представлении каталога **sys.server_principals** . Значение идентификатора безопасности уникально для каждого имени входа на сервере.|41|Да|  
|NTDomainName|`nvarchar`|Домен Windows, к которому принадлежит пользователь.|7|Да|  
|NTUserName|`nvarchar`|Имя пользователя Windows.|6|Да|  
|Offset|`int`|Начальное смещение инструкции в пределах хранимой процедуры или пакета.|61|Да|  
|ObjectID|`int`|Идентификатор устаревшего компонента.|22|Да|  
|ObjectName|`nvarchar`|Имя устаревшего компонента.|34|Да|  
|RequestID|`int`|Идентификатор запроса, содержащего инструкцию.|49|Да|  
|ServerName|`nvarchar`|Имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , для которого производится трассировка.|26|нет|  
|SessionLoginName|`nvarchar`|Имя входа пользователя, который инициировал сеанс. Например, если подключиться к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] под именем Имя_входа1 и выполнить инструкцию как пользователь с именем Имя_входа2, в столбце `SessionLoginName` выводится значение Имя_входа1, а в столбце `LoginName` — значение Имя_входа2. В этом столбце отображаются имена входа как на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , так и в Windows.|64|Да|  
|SPID|`int`|Идентификатор сеанса, в котором произошло событие.|12|Да|  
|SqlHandle|`image`|Двоичный дескриптор, который может быть использован для идентификации пакетов SQL или хранимых процедур.|63|Да|  
|StartTime|`datetime`|Время начала события, если оно известно.|14|Да|  
|TextData|`ntext`|Текстовое значение, зависящее от класса событий, фиксируемых при трассировке.|1|Да|  
|TransactionID|`bigint`|Назначенный системой идентификатор транзакции.|4|Да|  
|XactSequence|`bigint`|Токен, который описывает текущую транзакцию.|50|Да|  
  
## <a name="see-also"></a>См. также  
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)   
 [Класс событий объявления об устаревании](deprecation-announcement-event-class.md)   
 [Устаревшие функции компонента Database Engine в SQL Server 2014](../../database-engine/deprecated-database-engine-features-in-sql-server-2016.md)  
  
  
