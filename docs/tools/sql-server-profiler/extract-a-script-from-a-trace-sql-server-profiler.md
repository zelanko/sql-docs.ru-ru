---
title: Извлечение сценария из трассировки (приложение SQL Server Profiler) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- scripts [SQL Server], traces
- extracting script from trace [SQL Server]
ms.assetid: 431126a6-ff91-4818-8763-4442152bd571
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5cab84931db11e91e474ffd38aecfa4fb2aafae4
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62712461"
---
# <a name="extract-a-script-from-a-trace-sql-server-profiler"></a>извлечь скрипт из трассировки (приложение SQL Server Profiler)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В этом подразделе описано, как извлечь события [!INCLUDE[tsql](../../includes/tsql-md.md)] из файла или таблицы трассировки и сохранить их в виде скрипта [!INCLUDE[tsql](../../includes/tsql-md.md)] при помощи приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
### <a name="to-extract-a-transact-sql-script-from-a-trace-file-or-table"></a>Извлечение скрипта Transact-SQL из файла или таблицы трассировки:  
  
1.  Откройте файл трассировки или таблицы, содержащий события [!INCLUDE[tsql](../../includes/tsql-md.md)], которые необходимо сохранить в файле скрипта [!INCLUDE[tsql](../../includes/tsql-md.md)]. Дополнительные сведения см. в статье [Открыть файл трассировки (приложение SQL Server Profiler)](../../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md) или в помощник по настройке ядра СУБД [Открыть таблицу трассировки (приложение SQL Server Profiler)](../../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md).  
  
2.  В меню **Файл** выберите пункт **Экспорт**, затем **Извлечь события SQL Server** и щелкните **Извлечь события Transact-SQL**.  
  
3.  В диалоговом окне **Сохранить как** введите имя файла [!INCLUDE[tsql](../../includes/tsql-md.md)] и нажмите кнопку **Сохранить**.  
  
## <a name="see-also"></a>См. также:  
 [Приложение SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
