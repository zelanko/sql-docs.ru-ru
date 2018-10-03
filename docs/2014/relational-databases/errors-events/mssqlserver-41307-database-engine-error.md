---
title: MSSQLSERVER_41307 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41307 (Database Engine error)
ms.assetid: 56f56410-b07d-4379-b01c-702c95761070
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: aa0bf9ea69f6e38b06eb5723cc6c9058265ada50
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48095134"
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
 Максимальный размер строки оптимизированной для памяти таблицы составляет 8060 байт. Дополнительные сведения см. в статье [Размер строк и таблицы для таблиц, оптимизированных для памяти](../in-memory-oltp/memory-optimized-tables.md). Дополнительные сведения см. в разделе [In-Memory OLTP (оптимизация в памяти)](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
## <a name="see-also"></a>См. также  
 [Выполняющаяся в памяти OLTP (оптимизация в памяти)](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
