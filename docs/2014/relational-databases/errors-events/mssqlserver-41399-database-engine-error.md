---
title: MSSQLSERVER_41399 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41399 (Database Engine error)
ms.assetid: 5e5acb07-16ca-4329-8210-cd2bab0c904f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0c7314eb829880ed9689ac58330f286761dd6c57
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85053898"
---
# <a name="mssqlserver_41399"></a>MSSQLSERVER_41399
    
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
 [Выполняющаяся в памяти OLTP (оптимизация в памяти)](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
