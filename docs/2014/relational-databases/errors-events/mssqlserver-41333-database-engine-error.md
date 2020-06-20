---
title: MSSQLSERVER_41333 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41333 (Database Engine error)
ms.assetid: c3c3ae9a-1e4c-4de6-ba72-2f393375b053
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0fdc950e523fe1851aaf5664e2d40ff311a24ab7
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85032986"
---
# <a name="mssqlserver_41333"></a>MSSQLSERVER_41333
    
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
  
 Дополнительные сведения см. в разделе [In-Memory OLTP (оптимизация в памяти)](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
## <a name="see-also"></a>См. также:  
 [Выполняющаяся в памяти OLTP (оптимизация в памяти)](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
