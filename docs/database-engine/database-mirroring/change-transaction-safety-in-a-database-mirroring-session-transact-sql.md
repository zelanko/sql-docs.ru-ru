---
title: Изменение безопасности транзакций в сеансах зеркального отображения базы данных (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: database-mirroring
ms.reviewer: ''
ms.suite: sql
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- transaction safety [SQL Server database mirroring]
ms.assetid: 8b03bb82-8589-4558-8545-9942fe008391
caps.latest.revision: 38
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3f02def2d283fa72c7b05d052f1d3d0cce5a247d
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="change-transaction-safety-in-a-database-mirroring-session-transact-sql"></a>Изменение безопасности транзакций в сеансах зеркального отображения базы данных (Transact-SQL)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Безопасность транзакций является атрибутом, который контролирует режим работы сеанса. Однако в любой момент времени владелец базы данных может изменить безопасность транзакций. По умолчанию уровень безопасности транзакций установлен в FULL (синхронный режим работы).  
  
 Выключение безопасности транзакций переключает сеанс в асинхронный режим работы, что максимизирует производительность. Если участник становится недоступен, зеркало останавливается, но остается доступным в качестве «горячего» резервирования (переход на ресурс отработки отказа требует принудительного запуска службы с возможностью потери данных).  
  
### <a name="to-turn-on-transaction-safety"></a>Включение безопасности транзакций  
  
1.  Подключитесь к основному серверу.  
  
2.  Выполните следующую инструкцию Transact-SQL:  
  
    ```  
    ALTER DATABASE <database> SET PARTNER SAFETY FULL  
    ```  
  
     где *\<база_данных>* — имя зеркально отображаемой базы данных.  
  
### <a name="to-turn-off-transaction-safety"></a>Выключение безопасности транзакций  
  
1.  Подключитесь к основному серверу.  
  
2.  Выполните следующую инструкцию:  
  
    ```  
    ALTER DATABASE <database> SET PARTNER SAFETY OFF  
    ```  
  
     где *\<база_данных>* — зеркально отображаемая база данных.  
  
## <a name="see-also"></a>См. также:  
 [Зеркальное отображение базы данных ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-database-mirroring.md)   
 [Режимы работы зеркального отображения базы данных](../../database-engine/database-mirroring/database-mirroring-operating-modes.md)  
  
  
