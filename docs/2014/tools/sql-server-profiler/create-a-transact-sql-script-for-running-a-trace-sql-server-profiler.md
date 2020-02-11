---
title: Создание сценария Transact-SQL для выполнения трассировки (приложение SQL Server Profiler) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], running
- scripts [SQL Server], traces
ms.assetid: 6b0e2519-998d-40d5-b8ba-5e6a773f91a6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 948ef7eb5fdfeabdbb2ba3829e172f7c9f4028da
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "63255805"
---
# <a name="create-a-transact-sql-script-for-running-a-trace-sql-server-profiler"></a>создать скрипт Transact-SQL для выполнения трассировки (приложение SQL Server Profiler)
  В данном подразделе описан процесс создания скрипта Transact-SQL из существующего файла или таблицы трассировки при помощи приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
### <a name="to-create-a-transact-sql-script-to-run-a-trace"></a>Создание скрипта Transact-SQL для запуска трассировки  
  
1.  Откройте таблицу или файл трассировки. Дополнительные сведения см. в статье [Открыть файл трассировки (приложение SQL Server Profiler)](open-a-trace-file-sql-server-profiler.md) или в помощник по настройке ядра СУБД [Открыть таблицу трассировки (приложение SQL Server Profiler)](open-a-trace-table-sql-server-profiler.md).  
  
2.  В меню**Файл**выберите команду **Экспорт**, затем **Создать определение трассировки**и щелкните версию, соответствующую серверу, который необходимо трассировать.  
  
3.  В диалоговом окне **Сохранить как** введите имя файла скрипта и нажмите кнопку **Сохранить**.  
  
## <a name="see-also"></a>См. также:  
 [Шаблоны и разрешения приложения SQL Server Profiler](sql-server-profiler-templates-and-permissions.md)   
 [Приложение SQL Server Profiler](sql-server-profiler.md)  
  
  
