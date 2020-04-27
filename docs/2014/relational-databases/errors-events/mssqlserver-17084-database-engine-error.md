---
title: MSSQLSERVER_17084 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17084 (Database Engine error)
ms.assetid: e579d104-3307-4edd-8587-b14ecbc02ed9
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 95d0da610a8030c68bcf25d650e68aef4ae83128
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62915478"
---
# <a name="mssqlserver_17084"></a>MSSQLSERVER_17084
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|Идентификатор события|17084|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|P3_ATOMIC_WITH_MISSING_OPTION|  
|Текст сообщения|Предложение WITH инструкции BEGIN ATOMIC должно задавать значение для параметра «%ls».|  
  
## <a name="explanation"></a>Объяснение  
 Предложение WITH инструкции BEGIN ATOMIC не задает значение для параметра.  
  
## <a name="user-action"></a>Действие пользователя  
 Блоки `ATOMIC` требуют значений для параметров `WITH`, `TRANSACTION ISOLATION LEVEL` и `LANGUAGE`. Вот несколько примеров.  
  
```  
BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE= N'us_english')  
```  
  
 Дополнительные сведения см. в разделе [In-Memory OLTP (оптимизация в памяти)](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
## <a name="see-also"></a>См. также:  
 [Выполняющаяся в памяти OLTP (оптимизация в памяти)](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
