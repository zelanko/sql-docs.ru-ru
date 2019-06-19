---
title: MSSQLSERVER_2596 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2596 (Database Engine error)
ms.assetid: 49ab892f-8ba3-4ba1-b562-ddf205019802
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 21209de55bc010c2c85285f4cbed7305c6755f4c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62914371"
---
# <a name="mssqlserver2596"></a>MSSQLSERVER_2596
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|2596|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|DBCC_DATABASE_IN_READ_ONLY_MODE|  
|Текст сообщения|Инструкция восстановления не была обработана. База данных не может быть доступна только для чтения.|  
  
## <a name="explanation"></a>Объяснение  
 Это сообщение указывает, что база данных находится в режиме «только для чтения». Восстановление невозможно, если база данных находится в режиме «только для чтения».  
  
## <a name="user-action"></a>Действие пользователя  
 При помощи инструкции ALTER DATABASE переведите базу данных в режим чтения и записи, а затем повторите команду DBCC.  
  
## <a name="see-also"></a>См. также  
 [ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql)  
  
  
