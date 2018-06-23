---
title: MSSQLSERVER_2530 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5d4be07a-38a5-4b25-819c-4dcb4636cc15
caps.latest.revision: 11
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: ccf0b157984cce59ceff84fcff0c25a2f708e26f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36194273"
---
# <a name="mssqlserver2530"></a>MSSQLSERVER_2530
    
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
  
## <a name="see-also"></a>См. также  
 [Включение индексов и ограничений](../indexes/enable-indexes-and-constraints.md)   
 [ALTER INDEX (Transact-SQL)](/sql/t-sql/statements/alter-index-transact-sql)   
 [CREATE INDEX (Transact-SQL)](/sql/t-sql/statements/create-index-transact-sql)   
 [DBCC DBREINDEX (Transact-SQL)](/sql/t-sql/database-console-commands/dbcc-dbreindex-transact-sql)  
  
  
