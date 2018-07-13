---
title: Изменение безопасности транзакций в сеансах зеркального отображения базы данных (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- transaction safety [SQL Server database mirroring]
ms.assetid: 8b03bb82-8589-4558-8545-9942fe008391
caps.latest.revision: 35
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 17d9652ea08705f91d7ce6199ea39c14ca2d2afe
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37148975"
---
# <a name="change-transaction-safety-in-a-database-mirroring-session-transact-sql"></a>Изменение безопасности транзакций в сеансах зеркального отображения базы данных (Transact-SQL)
  Безопасность транзакций является атрибутом, который контролирует режим работы сеанса. Однако в любой момент времени владелец базы данных может изменить безопасность транзакций. По умолчанию уровень безопасности транзакций установлен в FULL (синхронный режим работы).  
  
 Выключение безопасности транзакций переключает сеанс в асинхронный режим работы, что максимизирует производительность. Если участник становится недоступен, зеркало останавливается, но остается доступным в качестве «горячего» резервирования (переход на ресурс отработки отказа требует принудительного запуска службы с возможностью потери данных).  
  
### <a name="to-turn-on-transaction-safety"></a>Включение безопасности транзакций  
  
1.  Подключитесь к основному серверу.  
  
2.  Выполните следующую инструкцию Transact-SQL:  
  
    ```  
    ALTER DATABASE <database> SET PARTNER SAFETY FULL  
    ```  
  
     где *\<база_данных>*  — имя зеркально отображаемой базы данных.  
  
### <a name="to-turn-off-transaction-safety"></a>Выключение безопасности транзакций  
  
1.  Подключитесь к основному серверу.  
  
2.  Выполните следующую инструкцию:  
  
    ```  
    ALTER DATABASE <database> SET PARTNER SAFETY OFF  
    ```  
  
     где *\<база_данных>*  — зеркально отображаемая база данных.  
  
## <a name="see-also"></a>См. также  
 [Зеркальное отображение базы данных ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring)   
 [Режимы работы зеркального отображения базы данных](database-mirroring-operating-modes.md)  
  
  
