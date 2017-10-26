---
title: "MSSQLSERVER_41333 | Документация Майкрософт"
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
- 41333 (Database Engine error)
ms.assetid: c3c3ae9a-1e4c-4de6-ba72-2f393375b053
caps.latest.revision: 7
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 72f5461f4e60b7e4c5cb53df75906d1aae0a07a5
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver41333"></a>MSSQLSERVER_41333
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|Идентификатор события|41333|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|CROSS_CONTAINER_ISOLATION_FAILURE|  
|Текст сообщения|Следующие транзакции должны принимать оптимизированные для памяти таблицы и скомпилированные в собственном коде хранимые процедуры в режиме изоляции моментальных снимков: транзакции RepeatableRead, транзакции Serializable и транзакции, которые обращаются к таблицам, не оптимизированным для памяти, в режиме изоляции RepeatableRead или Serializable.|  
  
## <a name="explanation"></a>Объяснение  
Между дисковыми транзакциями и XTP-транзакциями существуют ограничения для пользователей на более высоких уровнях изоляции.  
  
## <a name="user-action"></a>Действие пользователя  
Не пытайтесь выполнять операции с высоким уровнем изоляции в оптимизируемых для памяти (и хранимым процедурам, оптимизированным в собственном коде) и дисковых таблицах.  
  
Дополнительные сведения см. в разделе [In-Memory OLTP (оптимизация в памяти)](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
## <a name="see-also"></a>См. также:  
[Выполняющаяся в памяти OLTP &#40;оптимизация в памяти&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  

