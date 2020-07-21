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
ms.openlocfilehash: 6e2624eaa767a6607aa5a5fc81c65ddad29e77b0
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/21/2020
ms.locfileid: "86551339"
---
# <a name="mssqlserver_41399"></a>MSSQLSERVER_41399
    
## <a name="details"></a>Сведения  
  
|attribute|Значение|  
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
  
  
