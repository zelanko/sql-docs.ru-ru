---
title: "MSSQLSERVER_2596 | Документация Майкрософт"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 2596 (Database Engine error)
ms.assetid: 49ab892f-8ba3-4ba1-b562-ddf205019802
caps.latest.revision: "18"
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.openlocfilehash: 8eb8b851b589c916a449b527c8037e932d683472
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="mssqlserver2596"></a>MSSQLSERVER_2596
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|2596|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|DBCC_DATABASE_IN_READ_ONLY_MODE|  
|Текст сообщения|Инструкция восстановления не была обработана. База данных не может быть доступна только для чтения.|  
  
## <a name="explanation"></a>Объяснение  
Это сообщение указывает, что база данных находится в режиме «только для чтения». Восстановление невозможно, если база данных находится в режиме «только для чтения».  
  
## <a name="user-action"></a>Действие пользователя  
При помощи инструкции ALTER DATABASE переведите базу данных в режим чтения и записи, а затем повторите команду DBCC.  
  
## <a name="see-also"></a>См. также:  
[ALTER DATABASE (Transact-SQL)](~/t-sql/statements/alter-database-transact-sql-set-options.md)  
  
