---
title: MSSQLSERVER_2530 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
ms.assetid: 5d4be07a-38a5-4b25-819c-4dcb4636cc15
caps.latest.revision: 11
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0f3c112576fe769325c6ded074afd407d49ad340
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver2530"></a>MSSQLSERVER_2530
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|2530|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|DBCC_INDEX_IS_OFFLINE|  
|Текст сообщения|Индекс "%.*ls" для таблицы "%.\*ls" помечен как отключенный.|  
  
## <a name="explanation"></a>Объяснение  
Инструкция DBCC не может быть выполнена, так как отключен указанный индекс. После отключения индекс остается в отключенном состоянии до тех пор, пока он не будет перестроен или удален и создан повторно.  
  
## <a name="user-action"></a>Действие пользователя  
  
1.  Включить отключенный индекс одним из следующих способов.  
  
    -   Инструкцией ALTER INDEX с предложением REBUILD.  
  
    -   Инструкцией CREATE INDEX с предложением DROP_EXISTING.  
  
    -   DBCC DBREINDEX  
  
2.  Перезапустить инструкцию DBCC.  
  
## <a name="see-also"></a>См. также:  
[Включение индексов и ограничений](~/relational-databases/indexes/enable-indexes-and-constraints.md)  
[ALTER INDEX &#40;Transact-SQL&#41;](~/t-sql/statements/alter-index-transact-sql.md)  
[CREATE INDEX &#40;Transact-SQL&#41;](~/t-sql/statements/create-index-transact-sql.md)  
[DBCC DBREINDEX (Transact-SQL)](~/t-sql/database-console-commands/dbcc-dbreindex-transact-sql.md)  
  
