---
title: Окно "Потоки" | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.technology: scripting
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- vs.debug.threads
helpviewer_keywords:
- Threads Window [Transact-SQL]
ms.assetid: e153f619-0049-4162-9076-c24a454f3278
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 99fad1df0f1eab5ee6bd01f816ca9007c7d66f64
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2018
---
# <a name="transact-sql-debugger---threads-window"></a>Отладчик Transact-SQL, окно потоков
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  В окне **Потоки** отображаются сведения о потоке компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] , который используется в отлаживаемом сеансе редактора запросов компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] . Чтобы иметь возможность просматривать сведения о потоке, необходимо находиться в режиме отладки.  
  
## <a name="task-list"></a>Список задач  
 **Доступ к окну «Потоки»**  
  
-   В меню **Отладка** укажите **Окна**и выберите пункт **Потоки**.  
  
## <a name="columns"></a>Столбцы  
 **Идентификатор**  
 Уникальный идентификационный номер, присвоенный отладчиком [!INCLUDE[tsql](../../includes/tsql-md.md)] потоку. Чтобы получить дополнительные сведения о потоке, можно выбрать строки в динамическом административном представлении sys.dm_os_threads.  
  
 При работе не в режиме использования упрощенных пулов должна быть выполнена выборка строки, в которой значение os_thread_id совпадает со значением в столбце **Идентификатор** . При работе в режиме использования упрощенных пулов выберите строку, в которой значение fiber_context_address совпадает со значением в столбце **Идентификатор** .  
  
 **Название**  
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
  
## <a name="see-also"></a>См. также:  
 [Отладчик Transact-SQL](../../relational-databases/scripting/transact-sql-debugger.md)   
 [Сведения отладчика Transact-SQL](../../relational-databases/scripting/transact-sql-debugger-information.md)   
 [sys.dm_os_threads (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-os-threads-transact-sql.md)   
 [sys.sysprocesses (Transact-SQL)](../../relational-databases/system-compatibility-views/sys-sysprocesses-transact-sql.md)  
  
  
