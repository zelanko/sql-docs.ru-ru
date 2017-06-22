---
title: "MSSQLSERVER_41307 | Документация Майкрософт"
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
- 41307 (Database Engine error)
ms.assetid: 56f56410-b07d-4379-b01c-702c95761070
caps.latest.revision: 9
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: f0b0096029fd86def5eb2f44bdba4dcea418137c
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver41307"></a>MSSQLSERVER_41307
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|Идентификатор события|41307|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|HK_HEKATON_ROW_LIMIT|  
|Текст сообщения|Был превышен максимальный размер строки (*число* байт) для оптимизируемых для памяти таблиц. Упростите определение таблицы.|  
  
## <a name="explanation"></a>Объяснение  
Максимальный размер строки оптимизированной для памяти таблицы составляет 8060 байт. Дополнительные сведения см. в статье [Размер строк и таблицы для таблиц, оптимизированных для памяти](~/relational-databases/in-memory-oltp/table-and-row-size-in-memory-optimized-tables.md). Дополнительные сведения см. в разделе [In-Memory OLTP (оптимизация в памяти)](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
## <a name="see-also"></a>См. также:  
[Выполняющаяся в памяти OLTP &#40;оптимизация в памяти&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  

