---
title: MSSQLSERVER_41399 | Документация Майкрософт
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
- 41399 (Database Engine error)
ms.assetid: 5e5acb07-16ca-4329-8210-cd2bab0c904f
caps.latest.revision: 6
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e18e954e19b87656cce1dbf6099b96cc5701c30e
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="mssqlserver41399"></a>MSSQLSERVER_41399
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|Идентификатор события|41399|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|MAX_SORT_ROW_WIDTH_EXCEEDED|  
|Текст сообщения|Слишком сложная операция сортировки. Дополнительные сведения см. в электронной документации по SQL Server.|  
  
## <a name="explanation"></a>Объяснение  
Сортировка результата операций соединения и агрегации увеличивает сложность операции сортировки за счет увеличения размера строки в буфере сортировки. Эта ошибка означает, что размер строки превышает максимальный размер, поддерживаемый оператором сортировки в изначально скомпилированных хранимых процедурах. Обратите внимание, что размер строки в буфере сортировки определяется только количеством соединений и количеством и типом агрегатных функций. Размер строк в базовых таблицах не влияет на размер строки в буфере.  
  
## <a name="user-action"></a>Действие пользователя  
Уменьшить сложность запроса путем удаления соединений или агрегатных функций.  
  
## <a name="see-also"></a>См. также:  
[Выполняющаяся в памяти OLTP (оптимизация в памяти)](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
