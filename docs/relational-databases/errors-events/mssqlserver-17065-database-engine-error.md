---
title: "MSSQLSERVER_17065 | Документация Майкрософт"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 17065 (Database Engine error)
ms.assetid: 63c2ba5a-be34-461e-bee1-03c25b396cd2
caps.latest.revision: 16
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 2c423cd3e119d403d506cf45f0577ba68832d6b4
ms.lasthandoff: 04/11/2017

---
# <a name="mssqlserver17065"></a>MSSQLSERVER_17065
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|17065|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|SQLASSERT_BOTH|  
|Текст сообщения|Проверочное утверждение SQL Server: файл: \<%s>, строка = %d %s Ошибочное утверждение = "%s" %s. Возможно, эта ошибка связана со временем. Если ошибка не исчезнет после повторного выполнения инструкции, проверьте целостность структуры базы данных при помощи инструкции DBCC CHECKDB или перезапустите сервер, чтобы убедиться, что структуры данных в памяти не повреждены.|  
  
## <a name="explanation"></a>Объяснение  
Эта ошибка может быть вызвана нерегулярными проблемами, связанными со временем, или повреждением данных в памяти или на диске.  
  
## <a name="user-action"></a>Действие пользователя  
Выполните повторно инструкцию, которая вызвала появление исключения. Если ошибка вызвана событием, связанным со временем, она, возможно, не повторится. Если ошибка не исчезла, проверьте диск на наличие повреждений при помощи инструкции DBCC CHECKDB. Перезапустите сервер, чтобы убедиться, что структуры данных в памяти не повреждены.  
  
## <a name="see-also"></a>См. также:  
[DBCC CHECKDB (Transact-SQL)](~/t-sql/database-console-commands/dbcc-checkdb-transact-sql.md)  
  

