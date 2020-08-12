---
title: Извлечение скрипта из трассировки
titleSuffix: SQL Server Profiler
description: Узнайте, как извлечь события Transact-SQL из таблицы или файла трассировки в SQL Server Profiler и сохранить их в виде файла скрипта Transact-SQL.
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
ms.assetid: 431126a6-ff91-4818-8763-4442152bd571
author: markingmyname
ms.author: maghan
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.openlocfilehash: 2495eb7c020e6fb64fb894d4d6bb7614707f84bc
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85774866"
---
# <a name="extract-a-script-from-a-trace-sql-server-profiler"></a>извлечь скрипт из трассировки (приложение SQL Server Profiler)

 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

В этом подразделе описано, как извлечь события [!INCLUDE[tsql](../../includes/tsql-md.md)] из файла или таблицы трассировки и сохранить их в виде скрипта [!INCLUDE[tsql](../../includes/tsql-md.md)] при помощи приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
### <a name="to-extract-a-transact-sql-script-from-a-trace-file-or-table"></a>Извлечение скрипта Transact-SQL из файла или таблицы трассировки:  
  
1.  Откройте файл трассировки или таблицы, содержащий события [!INCLUDE[tsql](../../includes/tsql-md.md)] , которые необходимо сохранить в файле скрипта [!INCLUDE[tsql](../../includes/tsql-md.md)] . Дополнительные сведения см. в статье [Открыть файл трассировки (приложение SQL Server Profiler)](../../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md) или в помощник по настройке ядра СУБД [Открыть таблицу трассировки (приложение SQL Server Profiler)](../../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md).  
  
2.  В меню **Файл** выберите пункт **Экспорт**, затем **Извлечь события SQL Server**и щелкните **Извлечь события Transact-SQL**.  
  
3.  В диалоговом окне **Сохранить как** введите имя файла [!INCLUDE[tsql](../../includes/tsql-md.md)] и нажмите кнопку **Сохранить**.  
  
## <a name="see-also"></a>См. также:  
 [Приложение SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
