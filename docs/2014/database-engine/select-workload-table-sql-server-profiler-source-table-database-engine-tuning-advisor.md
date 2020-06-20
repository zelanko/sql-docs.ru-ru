---
title: SQL Server Profiler-Source Table-помощник по настройке ядра СУБД — выбор таблицы рабочей нагрузки | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.replay.tools.sourcetable.f1
helpviewer_keywords:
- Select Workload Table dialog box
- Source Table dialog box
ms.assetid: 51185be7-7092-480a-a52c-cf7786c4a0a0
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: c706613c828ce579af27a8c5a6890936a31814ca
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84929285"
---
# <a name="sql-server-profiler---source-table-database-engine-tuning-advisor---select-workload-table"></a>SQL Server Profiler-Source Table-помощник по настройке ядра СУБД — выбор таблицы рабочей нагрузки
  Microsoft [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] и помощник по настройке [!INCLUDE[ssDE](../includes/ssde-md.md)] используют это диалоговое окно для выбора таблиц.  
  
 В [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] диалоговое окно **Исходная таблица** используется для задания исходной таблицы для таблицы трассировки. Это таблица, из которой загружается трассировка, и содержимое которой просматривается или используется для воспроизведения трассировки.  
  
 В помощнике по настройке [!INCLUDE[ssDE](../includes/ssde-md.md)] диалоговое окно **Выбор таблицы рабочей нагрузки** используется для выбора таблицы базы данных, содержащей данные трассировки [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)], для использования в качестве рабочей нагрузки при настройке или для предварительного просмотра содержимого таблицы перед началом анализа настройки.  
  
## <a name="options"></a>Варианты  
 **SQL Server**  
 Указывает экземпляр [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , к которому в данный момент установлено подключение. Это поле заполняется автоматически и не может быть изменено.  
  
 **База данных**  
 Задайте базу данных, в которой расположена таблица трассировки.  
  
 **Владелец**  
 Specifies the owner of the trace table. Это поле автоматически заполняется значением **dbo**.  
  
 **Таблица**  
 Задайте имя таблицы трассировки, из которой должна читаться трассировка.  
  
## <a name="see-also"></a>См. также:  
 [Сохранение результатов трассировки в таблицу (приложение SQL Server Profiler)](../tools/sql-server-profiler/save-trace-results-to-a-table-sql-server-profiler.md)   
 [Шаблоны и разрешения приложения SQL Server Profiler](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)   
 [Database Engine Tuning Advisor](../relational-databases/performance/database-engine-tuning-advisor.md)  
  
  
