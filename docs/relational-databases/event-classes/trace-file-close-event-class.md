---
description: Trace File Close, класс событий
title: Класс событий Trace File Close | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- Trace File Close event class
ms.assetid: 128b7bac-cb64-43e7-ae9b-87b7d2ebb4ef
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: d745fcc8ce5c09b69e6c0b268956a409aeea07c3
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97483486"
---
# <a name="trace-file-close-event-class"></a>Trace File Close, класс событий
[!INCLUDE [SQL Server - ASDB](../../includes/applies-to-version/sql-asdb.md)]
   Класс событий **Trace File Close** указывает, что файл трассировки был закрыт во время переключения на файл продолжения трассировки.  
  
## <a name="trace-file-close-event-class-data-columns"></a>Столбцы данных класса событий Trace File Close  
  
|Имя столбца данных|Тип данных|Описание|Идентификатор столбца|Фильтруемый|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**EventClass**|**int**|Тип события = 150.|27|Нет|  
|**EventSequence**|**int**|Уникальная отметка времени события, возникшего в этой трассировке. Это число монотонно возрастает для каждого сработавшего события.|51|Нет|  
|**FileName**|**nvarchar**|Логическое имя закрываемого файла трассировки.|36|Да|  
|**IsSystem**|**int**|Указывает, произошло событие в системном или в пользовательском процессе. 1 = системный, NULL = пользовательский. Значение всегда равно 1 для этого класса событий.|60|Да|  
|**LoginName**|**nvarchar**|Имя входа пользователя (либо защищенное имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , либо учетные данные входа [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows в формате «ДОМЕН\имя_пользователя»). Значение всегда равно «sa» для этого класса событий.|11|Да|  
|**ObjectID**|**int**|Назначенный системой идентификатор трассировки.|22|Да|  
|**ServerName**|**nvarchar**|Имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , для которого производится трассировка.|26|Нет|  
|**SessionLoginName**|**nvarchar**|Имя входа пользователя, создавшего этот сеанс. Например, при подключении к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] по имени "Имя_входа1" и при выполнении инструкции под именем "Имя_входа2" **SessionLoginName** содержит значение "Имя_входа1", а **LoginName** — значение "Имя_входа2". В этом столбце отображаются как имена входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , так и имена входа Windows.|64|Да|  
|**SPID**|**int**|Идентификатор сеанса, в котором произошло событие.|12|Да|  
|**StartTime**|**datetime**|Время начала события, если оно известно.|14|Да|  
  
## <a name="see-also"></a>См. также:  
 [Хранимая процедура sp_trace_setevent (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)  
  
  
