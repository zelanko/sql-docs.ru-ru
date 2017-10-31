---
title: "MSSQLSERVER_41332 | Документация Майкрософт"
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
- 41332 (Database Engine error)
ms.assetid: d3403c3e-d178-4006-b6c9-c18609562db5
caps.latest.revision: 7
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: be21e36f47e2bae00387e1f5aed087c94688f930
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver41332"></a>MSSQLSERVER_41332
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|Идентификатор события|41332|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|SQL_SNAPSHOT_NOT_SUPPORTED|  
|Текст сообщения|Если для сеанса TRANSACTION ISOLATION LEVEL задано значение SNAPSHOT, нельзя создать оптимизированные для памяти таблицы и скомпилированные в собственном коде хранимые процедуры или получать к ним доступ.|  
  
## <a name="explanation"></a>Объяснение  
Транзакция была запущена на уровне изоляции моментального снимка, а затем попыталась использовать несовместимую функцию.  
  
## <a name="user-action"></a>Действие пользователя  
Запустите транзакцию с другим уровнем изоляции. Дополнительные сведения см. в разделе [In-Memory OLTP (оптимизация в памяти)](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
## <a name="see-also"></a>См. также:  
[Выполняющаяся в памяти OLTP &#40;оптимизация в памяти&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  

