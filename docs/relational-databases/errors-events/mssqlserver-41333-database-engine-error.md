---
title: MSSQLSERVER_41333 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 41333 (Database Engine error)
ms.assetid: c3c3ae9a-1e4c-4de6-ba72-2f393375b053
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a4e5e6d6b8e7b8fb62c3e7e8948bad8ecf5b0af2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62716491"
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
|Текст сообщения|Следующие транзакции должны обращаться к таблицам, оптимизируемым для памяти, и к скомпилированным в собственном коде хранимым процедурам с уровнем изоляции моментального снимка: транзакции RepeatableRead, транзакции Serializable и транзакции, которые обращаются к не оптимизированным для памяти таблицам с уровнем изоляции RepeatableRead или Serializable.|  
  
## <a name="explanation"></a>Объяснение  
Между дисковыми транзакциями и XTP-транзакциями существуют ограничения для пользователей на более высоких уровнях изоляции.  
  
## <a name="user-action"></a>Действие пользователя  
Не пытайтесь выполнять операции с высоким уровнем изоляции в оптимизируемых для памяти (и хранимым процедурам, оптимизированным в собственном коде) и дисковых таблицах.  
  
Дополнительные сведения см. в разделе [In-Memory OLTP (оптимизация в памяти)](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
## <a name="see-also"></a>См. также:  
[Выполняющаяся в памяти OLTP (оптимизация в памяти)](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
