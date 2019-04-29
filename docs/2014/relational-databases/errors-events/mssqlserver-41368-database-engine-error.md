---
title: MSSQLSERVER_41368 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41368 (Database Engine error)
ms.assetid: abc71559-4c4d-4cce-a08f-3299dd167842
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a2206980d241d3ef0aa683e4f987a4e337a86855
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62913809"
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
 Доступ к оптимизированным для памяти таблицам с уровнем изоляции READ COMMITTED поддерживается только для транзакций с автоматической фиксацией. Дополнительные сведения см. в разделе [Transaction Isolation Levels](../../database-engine/transaction-isolation-levels.md).  
  
 При доступе к оптимизированной для памяти таблицы из явной транзакции, начатой с помощью BEGIN TRANSACTION, или из неявной транзакции, если параметр IMPLICIT_TRANSACTIONS имеет значение ON, уровень изоляции READ COMMITTED не поддерживается.  
  
## <a name="user-action"></a>Действие пользователя  
 При доступе к оптимизированной для памяти таблице из явной или неявной транзакции с изоляцией READ COMMITTED, используйте для доступа к таблице моментальный снимок (SNAPSHOT). Это можно сделать с помощью табличной подсказки WITH (SNAPSHOT) (Дополнительные сведения см. в разделе [уровни изоляции транзакций с таблицами, оптимизированными для памяти, касающиеся](../in-memory-oltp/memory-optimized-tables.md)) или установив эту базу данных параметр MEMORY_OPTIMIZED_ELEVATE_TO_ Моментальный СНИМОК в значение ON (Дополнительные сведения см. в разделе [параметры ALTER DATABASE SET &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)).  
  
## <a name="see-also"></a>См. также  
 [Выполняющаяся в памяти OLTP (оптимизация в памяти)](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
