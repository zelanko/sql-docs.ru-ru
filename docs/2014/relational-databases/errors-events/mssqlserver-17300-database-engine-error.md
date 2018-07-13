---
title: MSSQLSERVER_17300 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 17300 (Database Engine error)
ms.assetid: c1d6bfb6-28af-4df6-8087-25807602d282
caps.latest.revision: 18
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 34a0cf19f43561f80e9822cdf34dd43793d869c2
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37431373"
---
# <a name="mssqlserver17300"></a>MSSQLSERVER_17300
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|17300|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|PROC_OUT_OF_SYSTASK_SESSIONS|  
|Текст сообщения|SQL Server не удалось запустить новую системную задачу либо из-за недостатка памяти, либо из-за превышения заданного в конфигурации максимального числа сеансов, допустимого для сервера. Проверьте, что на сервере достаточно памяти. Используйте хранимую процедуру sp_configure с параметром «user connections», чтобы выяснить максимально допустимое число соединений пользователя. Текущее число сеансов, включая пользовательские процессы, можно получить из представления sys.dm_exec_sessions.|  
  
## <a name="explanation"></a>Объяснение  
 Не удалось запустить новую системную задачу либо из-за недостатка памяти, либо из-за превышения заданного в конфигурации числа сеансов для сервера.  
  
## <a name="user-action"></a>Действие пользователя  
 Проверьте, что на сервере достаточно памяти. Проверьте текущее число системных задач с помощью представления sys.dm_exec_sessions и проверьте заданное значение максимального числа соединений пользователя с помощью хранимой процедуры sp_configure.  
  
 При необходимости выполните следующие действия.  
  
-   Добавьте память на сервер.  
  
-   Завершите один или несколько сеансов.  
  
-   Увеличьте максимально допустимое число одновременно подключенных пользователей на сервере.  
  
## <a name="see-also"></a>См. также  
 [sp_configure (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sys.dm_exec_sessions (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql)   
 [Настройка параметра конфигурации сервера user connections](../../database-engine/configure-windows/configure-the-user-connections-server-configuration-option.md)   
 [KILL (Transact-SQL)](/sql/t-sql/language-elements/kill-transact-sql)  
  
  
