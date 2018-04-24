---
title: MSSQLSERVER_41333 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 41333 (Database Engine error)
ms.assetid: c3c3ae9a-1e4c-4de6-ba72-2f393375b053
caps.latest.revision: 7
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5cc570e4313ffb253f244af9f7d8e3a314f767cd
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="mssqlserver41333"></a>MSSQLSERVER_41333
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
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
[Выполняющаяся в памяти OLTP (оптимизация в памяти)](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
