---
title: MSSQLSERVER_41332 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 41332 (Database Engine error)
ms.assetid: d3403c3e-d178-4006-b6c9-c18609562db5
caps.latest.revision: 7
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d871813734e6e514b30f4cf11508c2e50e07771c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36087862"
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
 Запустите транзакцию с другим уровнем изоляции. Дополнительные сведения см. в разделе [In-Memory OLTP (оптимизация в памяти)](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
## <a name="see-also"></a>См. также  
 [Выполняющаяся в памяти OLTP (оптимизация в памяти)](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  