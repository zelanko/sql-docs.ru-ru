---
title: Настройка зеркальной базы данных для использование свойства Trustworthy (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- TRUSTWORTHY database option
- mirror database [SQL Server]
- database mirroring [SQL Server], security
ms.assetid: 6993b076-78ef-453e-b0ea-e341b8e5ee3e
caps.latest.revision: 14
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 153bda8f9be87dfebff90f1f40974f248a094575
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36190291"
---
# <a name="set-up-a-mirror-database-to-use-the-trustworthy-property-transact-sql"></a>Настройка зеркальной базы данных на использование свойства TRUSTWORTHY (Transact-SQL)
  При резервном копировании базы данных ее свойство TRUSTWORTHY принимает значение OFF. Поэтому в новой зеркальной базе данных оно всегда будет иметь значение OFF. Если для базы данных после отработки отказа с переходом на другой ресурс требуется доверие, это потребует дополнительных действий по настройке после начала зеркального отображения.  
  
> [!NOTE]  
>  Дополнительные сведения об этом свойстве базы данных см. в разделе [Свойство базы данных TRUSTWORTHY](../../relational-databases/security/trustworthy-database-property.md).  
  
## <a name="procedure"></a>Процедура  
  
#### <a name="to-setup-a-mirror-database-to-use-the-trustworthy-property"></a>Настройка зеркальной базы данных на использование свойства TRUSTWORTHY  
  
1.  На основном экземпляре сервера необходимо убедиться, что свойство TRUSTWORTHY основной базы данных включено.  
  
    ```  
    SELECT name, database_id, is_trustworthy_on FROM sys.databases   
    ```  
  
     Дополнительные сведения см. в разделе [sys.databases (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql).  
  
2.  После начала зеркального отображения базы данных необходимо убедиться, что в этот момент база данных является основной, в сеансе используется синхронный режим работы и что сеанс уже синхронизирован.   
  
    ```  
    SELECT database_id, mirroring_role, mirroring_safety_level_desc, mirroring_state_desc FROM sys.database_mirroring  
    ```  
  
     Дополнительные сведения см. в разделе [sys.database_mirroring (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-database-mirroring-transact-sql).  
  
3.  Как только завершится синхронизация сеанса зеркального отображения, вручную переключитесь к зеркальной базе данных.  
  
     Сделать это можно в среде SQL Server Management Studio или при помощи Transact-SQL:  
  
    -   [Переключение сеанса зеркального отображения базы данных на другой ресурс вручную (среда SQL Server Management Studio)](manually-fail-over-a-database-mirroring-session-sql-server-management-studio.md)  
  
    -   [Переключение сеанса зеркального отображения базы данных на другой ресурс вручную (язык Transact-SQL)](manually-fail-over-a-database-mirroring-session-transact-sql.md)  
  
4.  Следующей командой ALTER DATABASE включите свойство TRUSTWORTHY для базы данных:  
  
    ```  
    ALTER DATABASE <database_name> SET TRUSTWORTHY ON  
    ```  
  
     Дополнительные сведения см. в разделе [ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql).  
  
5.  При необходимости можно вручную выполнить отработку отказа, чтобы вернуться к исходному участнику.  
  
6.  Кроме того, можно переключиться в асинхронный режим высокой производительности, для чего свойство SAFETY следует установить в значение OFF и проверить, что свойство WITNESS также установлено в значение OFF.  
  
     На языке Transact-SQL:  
  
    -   [Изменение безопасности транзакций в сеансах зеркального отображения базы данных (Transact-SQL)](change-transaction-safety-in-a-database-mirroring-session-transact-sql.md)  
  
    -   [Удаление следящего сервера из сеанса зеркального отображения базы данных (SQL Server)](remove-the-witness-from-a-database-mirroring-session-sql-server.md)  
  
     В среде SQL Server Management Studio:  
  
    -   [Создание сеанса зеркального отображения базы данных с использованием проверки подлинности Windows (среда SQL Server Management Studio)](establish-database-mirroring-session-windows-authentication.md)  
  
## <a name="see-also"></a>См. также  
 [Свойство базы данных TRUSTWORTHY](../../relational-databases/security/trustworthy-database-property.md)   
 [Настройка зашифрованной зеркальной базы данных](set-up-an-encrypted-mirror-database.md)  
  
  
