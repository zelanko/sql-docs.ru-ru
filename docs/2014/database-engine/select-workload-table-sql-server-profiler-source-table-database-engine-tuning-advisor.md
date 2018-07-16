---
title: SQL Server Profiler - источника базы данных таблиц помощника по настройке ядра — Выбор таблицы рабочей нагрузки | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.pro.replay.tools.sourcetable.f1
helpviewer_keywords:
- Select Workload Table dialog box
- Source Table dialog box
ms.assetid: 51185be7-7092-480a-a52c-cf7786c4a0a0
caps.latest.revision: 19
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8c371644630c24946b4acc50d77916fb8d0fd4a4
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37285690"
---
# <a name="sql-server-profiler---source-table-database-engine-tuning-advisor---select-workload-table"></a>SQL Server Profiler - источника базы данных таблиц помощника по настройке ядра — Выбор таблицы рабочей нагрузки
  Microsoft [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] и помощник по настройке [!INCLUDE[ssDE](../includes/ssde-md.md)] используют это диалоговое окно для выбора таблиц.  
  
 В [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] диалоговое окно **Исходная таблица** используется для задания исходной таблицы для таблицы трассировки. This is a table from which a trace is loaded, and the contents of which are viewed or used for replaying the trace.  
  
 В помощнике по настройке [!INCLUDE[ssDE](../includes/ssde-md.md)] диалоговое окно **Выбор таблицы рабочей нагрузки** используется для выбора таблицы базы данных, содержащей данные трассировки [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)], для использования в качестве рабочей нагрузки при настройке или для предварительного просмотра содержимого таблицы перед началом анализа настройки.  
  
## <a name="options"></a>Параметры  
 **SQL Server**  
 Указывает экземпляр [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], к которому в данный момент установлено подключение. Это поле заполняется автоматически и не может быть изменено.  
  
 **База данных**  
 Задайте базу данных, в которой расположена таблица трассировки.  
  
 **Владелец**  
 Specifies the owner of the trace table. Это поле автоматически заполняется значением **dbo**.  
  
 **Таблица**  
 Задайте имя таблицы трассировки, из которой должна читаться трассировка.  
  
## <a name="see-also"></a>См. также  
 [Сохранение результатов трассировки в таблицу &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/save-trace-results-to-a-table-sql-server-profiler.md)   
 [Шаблоны и разрешения приложения SQL Server Profiler](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)   
 [помощник по настройке ядра СУБД](../relational-databases/performance/database-engine-tuning-advisor.md)  
  
  
