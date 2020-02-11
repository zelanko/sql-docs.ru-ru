---
title: MSSQLSERVER_2530 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
ms.assetid: 5d4be07a-38a5-4b25-819c-4dcb4636cc15
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8058c7c31c49935d244726bf9e8ea0ac6cfbe750
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62914575"
---
# <a name="mssqlserver_2530"></a>MSSQLSERVER_2530
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
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
 [Включение индексов и ограничений](../indexes/enable-indexes-and-constraints.md)   
 [Инструкция ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)   
 [CREATE INDEX (Transact-SQL)](/sql/t-sql/statements/create-index-transact-sql)   
 [DBCC DBREINDEX (Transact-SQL)](/sql/t-sql/database-console-commands/dbcc-dbreindex-transact-sql)  
  
  
