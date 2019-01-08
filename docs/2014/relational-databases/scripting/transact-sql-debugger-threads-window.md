---
title: Окно "Потоки" | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- Threads Window [Transact-SQL]
ms.assetid: e153f619-0049-4162-9076-c24a454f3278
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 713fa85a342613f261bb53aa393b8ff1504d256b
ms.sourcegitcommit: 40c3b86793d91531a919f598dd312f7e572171ec
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/13/2018
ms.locfileid: "53328734"
---
# <a name="threads-window"></a>Окно потоков
  В окне **Потоки** отображаются сведения о потоке компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] , который используется в отлаживаемом сеансе редактора запросов компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] . Чтобы иметь возможность просматривать сведения о потоке, необходимо находиться в режиме отладки.  
  
## <a name="task-list"></a>Список задач  
 **Доступ к окну «Потоки»**  
  
-   В меню **Отладка** укажите **Окна**и выберите пункт **Потоки**.  
  
## <a name="columns"></a>Столбцы  
 **Идентификатор**  
 Уникальный идентификационный номер, присвоенный отладчиком [!INCLUDE[tsql](../../includes/tsql-md.md)] потоку. Чтобы получить дополнительные сведения о потоке, можно выбрать строки в динамическом административном представлении sys.dm_os_threads.  
  
 При работе не в режиме использования упрощенных пулов должна быть выполнена выборка строки, в которой значение os_thread_id совпадает со значением в столбце **Идентификатор** . При работе в режиме использования упрощенных пулов выберите строку, в которой значение fiber_context_address совпадает со значением в столбце **Идентификатор** .  
  
 **Name**  
 Выводится информация о сеансе компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] в формате **ИмяКомпьютера/ИмяЭкземпляра [SPID]**.  
  
 **ИмяКомпьютера**  
 Имя компьютера, на котором работает экземпляр компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] , к которому подключен сеанс редактора запросов.  
  
 **InstanceName**  
 Имя экземпляра, к которому подключен сеанс редактора запросов компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] .  
  
 **[SPID]**  
 Идентификатор процесса сеанса [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , который однозначно определяет этот сеанс. Можно получить дополнительные сведения об этом сеансе путем выборки строки в представлении sys.sysprocesses, которая имеет то же значение в столбце spid.  
  
 **Местоположение**  
 Отображается имя файла скрипта, который используется в отлаживаемом сеансе редактора запросов.  
  
 **Приоритет**  
 Отладчик [!INCLUDE[tsql](../../includes/tsql-md.md)] не поддерживает эту функцию.  
  
 **Приостановить**  
 Отладчик [!INCLUDE[tsql](../../includes/tsql-md.md)] не поддерживает эту функцию.  
  
## <a name="see-also"></a>См. также  
 [Отладчик Transact-SQL](transact-sql-debugger.md)   
 [Сведения отладчика Transact-SQL](transact-sql-debugger-information.md)   
 [sys.dm_os_threads (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-threads-transact-sql)   
 [sys.sysprocesses (Transact-SQL)](/sql/relational-databases/system-compatibility-views/sys-sysprocesses-transact-sql)  
