---
title: "MSSQLSERVER_8651 | Документация Майкрософт"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 8651 (Database Engine error)
ms.assetid: 4cc3498d-5449-4c4e-b1f9-3271831c725a
caps.latest.revision: 19
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 301cff27085ef62a3011bfef1103aca00b44d93b
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver8651"></a>MSSQLSERVER_8651
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|8651|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|MEMGRANT_ERR|  
|Текст сообщения|Не удалось выполнить запрошенную операцию, потому что недоступна минимально необходимая память для запроса. Уменьшите значение параметра конфигурации сервера «min memory per query».|  
  
## <a name="explanation"></a>Объяснение  
Память сервера потребляют другие процессы (усиливая нагрузку на память на сервере).  
  
## <a name="user-action"></a>Действие пользователя  
Уменьшите значение параметра конфигурации сервера «min memory per query» или снизьте интенсивность запросов на сервере.  
  
Далее представлены общие шаги, которые помогут при устранении неполадок с памятью.  
  
1.  Проверьте, не используют ли память данного сервера другие приложения или службы. Измените настройки таким образом, чтобы менее важные приложения или службы использовали меньший объем памяти.  
  
2.  Начните сбор счетчиков системного монитора для **SQL Server: диспетчер буферов**, **SQL Server: диспетчер памяти**.  
  
3.  Проверьте следующие параметры конфигурации памяти [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
    -   **max server memory**  
  
    -   **min server memory**  
  
    -   **min memory per query**  
  
    Обратите внимание на нестандартные параметры. При необходимости измените их. Параметры по умолчанию приведены в разделе «Настройка параметров конфигурации сервера» электронной документации по SQL Server.  
  
4.  Проверьте рабочую нагрузку (например, число параллельных сеансов, в текущий момент выполняющих запросы).  
  
Следующие действия могут позволить использовать больший объем памяти в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
-   Если какие-либо отличные от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] приложения используют необходимые ресурсы, попытайтесь прекратить выполнение этих приложений или перенесите их выполнение на отдельный сервер. Это снизит внешнюю нагрузку на память.  
  
-   Если установлен параметр **max server memory**, увеличьте его значение.  
  
Выполните следующие команды DBCC для освобождения нескольких кэшей памяти [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   DBCC FREESYSTEMCACHE  
  
-   DBCC FREESESSIONCACHE  
  
-   DBCC FREEPROCCACHE  
  
Если проблема не исчезла, необходимо продолжить ее исследование и, возможно, снизить рабочую нагрузку.  
  
## <a name="see-also"></a>См. также:  
[DBCC FREESYSTEMCACHE (Transact-SQL)](~/t-sql/database-console-commands/dbcc-freesystemcache-transact-sql.md)  
[DBCC FREESESSIONCACHE (Transact-SQL)](~/t-sql/database-console-commands/dbcc-freesessioncache-transact-sql.md)  
[DBCC FREEPROCCACHE &#40;Transact-SQL&#41;](~/t-sql/database-console-commands/dbcc-freeproccache-transact-sql.md)  
[Параметры конфигурации сервера (SQL Server)](~/database-engine/configure-windows/server-configuration-options-sql-server.md)  
[SQL Server, объект Buffer Manager](~/relational-databases/performance-monitor/sql-server-buffer-manager-object.md)  
[SQL Server, объект Memory Manager](~/relational-databases/performance-monitor/sql-server-memory-manager-object.md)  
  

