---
title: MSSQLSERVER_17067 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17067 (Database Engine error)
ms.assetid: 32c1f0e8-db70-4836-95b2-8833be9e0ad1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4ff3de7ed2fbe54a32aaa501979a3acb6b452947
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84967904"
---
# <a name="mssqlserver_17067"></a>MSSQLSERVER_17067
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|17067|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|SQLASSERT_MESG|  
|Текст сообщения|Утверждение SQL Server: файл: \<%s> , строка =% d% s. Возможно, эта ошибка связана со временем. Если ошибка не исчезнет после повторного выполнения инструкции, проверьте целостность структуры базы данных при помощи инструкции DBCC CHECKDB или перезапустите сервер, чтобы убедиться, что структуры данных в памяти не повреждены.|  
  
## <a name="explanation"></a>Объяснение  
 Эта ошибка может быть вызвана нерегулярными проблемами, связанными со временем, или повреждением данных в памяти или на диске.  
  
## <a name="user-action"></a>Действие пользователя  
 Выполните повторно инструкцию, которая вызвала появление исключения. Если ошибка вызвана событием, связанным со временем, она, возможно, не повторится. Если ошибка не исчезла, проверьте диск на наличие повреждений при помощи инструкции DBCC CHECKDB. Перезапустите сервер, чтобы убедиться, что структуры данных в памяти не повреждены.  
  
## <a name="see-also"></a>См. также:  
 [DBCC CHECKDB (Transact-SQL)](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)  
  
  
