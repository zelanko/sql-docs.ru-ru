---
title: "MSSQLSERVER_41368 | Документация Майкрософт"
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
- 41368 (Database Engine error)
ms.assetid: abc71559-4c4d-4cce-a08f-3299dd167842
caps.latest.revision: 9
author: BYHAM
ms.author: rickbyh
manager: jhubbard
robots: noindex,nofollow
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 9161b32ff6c9c2e2ee03b5909ee69db1594bbd9d
ms.contentlocale: ru-ru
ms.lasthandoff: 04/11/2017

---
# <a name="mssqlserver41368"></a>MSSQLSERVER_41368
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|Идентификатор события|41368|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|SQL_IMPLICIT_AND_EXPLICIT_TX_NOT_SUPPORTED|  
|Текст сообщения|Доступ к оптимизированным для памяти таблицам с уровнем изоляции READ COMMITTED поддерживается только для транзакций с автоматической фиксацией. Он не поддерживается для явных или неявных транзакций. Обеспечьте поддерживаемый уровень изоляции для оптимизированной для памяти таблицы с помощью табличного указания, например WITH (SNAPSHOT).|  
  
## <a name="explanation"></a>Объяснение  
Доступ к оптимизированным для памяти таблицам с уровнем изоляции READ COMMITTED поддерживается только для транзакций с автоматической фиксацией. Дополнительные сведения см. в статье об [операциях с таблицами и процедурами в памяти](~/relational-databases/in-memory-oltp/transactions-with-memory-optimized-tables.md).  
  
При доступе к оптимизированной для памяти таблицы из явной транзакции, начатой с помощью BEGIN TRANSACTION, или из неявной транзакции, если параметр IMPLICIT_TRANSACTIONS имеет значение ON, уровень изоляции READ COMMITTED не поддерживается.  
  
## <a name="user-action"></a>Действие пользователя  
При доступе к оптимизированной для памяти таблице из явной или неявной транзакции с изоляцией READ COMMITTED, используйте для доступа к таблице моментальный снимок (SNAPSHOT). Это можно сделать с помощью табличной подсказки WITH (SNAPSHOT) (Дополнительные сведения см. в статье о [транзакциях с таблицами и процедурами в памяти](~/relational-databases/in-memory-oltp/transactions-with-memory-optimized-tables.md)) или установив параметр MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT в значение ON (Дополнительные сведения см. в статье о [параметрах ALTER DATABASE SET (Transact-SQL)](~/t-sql/statements/alter-database-transact-sql.md)).  
  
## <a name="see-also"></a>См. также:  
[Выполняющаяся в памяти OLTP &#40;оптимизация в памяти&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  

