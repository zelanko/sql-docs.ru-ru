---
title: MSSQLSERVER_17066 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 17066 (Database Engine error)
ms.assetid: 7d650bbf-c583-4af8-9e22-993ee2880d95
caps.latest.revision: 16
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: f366eb8fbb486f836b7cfc8f0d92ffb1b0fe5023
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36087135"
---
# <a name="mssqlserver17066"></a>MSSQLSERVER_17066
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|17066|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|SQLASSERT_ONLY|  
|Текст сообщения|Проверочное утверждение SQL Server: файл: \<%s>, строка = %d %s Ошибочное утверждение = "%s". Возможно, эта ошибка связана со временем. Если ошибка не исчезнет после повторного выполнения инструкции, проверьте целостность структуры базы данных при помощи инструкции DBCC CHECKDB или перезапустите сервер, чтобы убедиться, что структуры данных в памяти не повреждены.|  
  
## <a name="explanation"></a>Объяснение  
 Эта ошибка может быть вызвана нерегулярными проблемами, связанными со временем, или повреждением данных в памяти или на диске.  
  
## <a name="user-action"></a>Действие пользователя  
 Выполните повторно инструкцию, которая вызвала появление исключения. Если ошибка вызвана событием, связанным со временем, она, возможно, не повторится. Если ошибка не исчезла, проверьте диск на наличие повреждений при помощи инструкции DBCC CHECKDB. Перезапустите сервер, чтобы убедиться, что структуры данных в памяти не повреждены.  
  
## <a name="see-also"></a>См. также  
 [DBCC CHECKDB (Transact-SQL)](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)  
  
  
