---
title: "Создать скрипт Transact-SQL для выполнения трассировки (приложение SQL Server Profiler) | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- traces [SQL Server], running
- scripts [SQL Server], traces
ms.assetid: 6b0e2519-998d-40d5-b8ba-5e6a773f91a6
caps.latest.revision: 25
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: dac4e6f11ed6bb9bf5c7de2cd2780553cfe972f2
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="create-a-transact-sql-script-for-running-a-trace-sql-server-profiler"></a>создать скрипт Transact-SQL для выполнения трассировки (приложение SQL Server Profiler)
  В данном подразделе описан процесс создания скрипта Transact-SQL из существующего файла или таблицы трассировки при помощи приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
### <a name="to-create-a-transact-sql-script-to-run-a-trace"></a>Создание скрипта Transact-SQL для запуска трассировки  
  
1.  Откройте таблицу или файл трассировки. Дополнительные сведения см. в статье [Открытие файла трассировки (приложение SQL Server Profiler)](../../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md) или [Открытие таблицы трассировки (приложение SQL Server Profiler)](../../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md).  
  
2.  В меню**Файл**выберите команду **Экспорт**, затем **Создать определение трассировки**и щелкните версию, соответствующую серверу, который необходимо трассировать.  
  
3.  В диалоговом окне **Сохранить как** введите имя файла скрипта и нажмите кнопку **Сохранить**.  
  
## <a name="see-also"></a>См. также:  
 [Шаблоны и разрешения приложения SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)   
 [Приложение SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
