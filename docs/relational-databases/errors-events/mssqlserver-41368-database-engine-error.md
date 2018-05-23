---
title: MSSQLSERVER_41368 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 41368 (Database Engine error)
ms.assetid: abc71559-4c4d-4cce-a08f-3299dd167842
caps.latest.revision: 9
author: MashaMSFT
ms.author: mathoma
manager: craigg
robots: noindex,nofollow
ms.openlocfilehash: f635eecdbaab6cbcb078fa59992928a66315a736
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2018
---
# <a name="mssqlserver41368"></a>MSSQLSERVER_41368
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
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
[Выполняющаяся в памяти OLTP (оптимизация в памяти)](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
