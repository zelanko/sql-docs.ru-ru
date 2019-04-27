---
title: Изменение безопасности транзакций в сеансах зеркального отображения базы данных (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- transaction safety [SQL Server database mirroring]
ms.assetid: 8b03bb82-8589-4558-8545-9942fe008391
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: a79010a4fa59eaebfc743543799a1e83cc5e687d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62754929"
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
  
  
