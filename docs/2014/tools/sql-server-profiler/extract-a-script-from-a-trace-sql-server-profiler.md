---
title: Извлечение сценария из трассировки (приложение SQL Server Profiler) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
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
ms.openlocfilehash: 178fba1888c84471b8cc568c77abd9ed797d1b6c
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52768286"
---
# <a name="extract-a-script-from-a-trace-sql-server-profiler"></a>извлечь скрипт из трассировки (приложение SQL Server Profiler)
  В этом подразделе описано, как извлечь события [!INCLUDE[tsql](../../includes/tsql-md.md)] из файла или таблицы трассировки и сохранить их в виде скрипта [!INCLUDE[tsql](../../includes/tsql-md.md)] при помощи приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
### <a name="to-extract-a-transact-sql-script-from-a-trace-file-or-table"></a>Извлечение скрипта Transact-SQL из файла или таблицы трассировки:  
  
1.  Откройте файл трассировки или таблицы, содержащий события [!INCLUDE[tsql](../../includes/tsql-md.md)], которые необходимо сохранить в файле скрипта [!INCLUDE[tsql](../../includes/tsql-md.md)]. Дополнительные сведения см. в статье [Открыть файл трассировки (приложение SQL Server Profiler)](open-a-trace-file-sql-server-profiler.md) или в помощник по настройке ядра СУБД [Открыть таблицу трассировки (приложение SQL Server Profiler)](open-a-trace-table-sql-server-profiler.md).  
  
2.  В меню **Файл** выберите пункт **Экспорт**, затем **Извлечь события SQL Server** и щелкните **Извлечь события Transact-SQL**.  
  
3.  В диалоговом окне **Сохранить как** введите имя файла [!INCLUDE[tsql](../../includes/tsql-md.md)] и нажмите кнопку **Сохранить**.  
  
## <a name="see-also"></a>См. также  
 [Приложение SQL Server Profiler](sql-server-profiler.md)  
  
  
