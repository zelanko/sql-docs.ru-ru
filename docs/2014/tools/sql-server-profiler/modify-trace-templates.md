---
title: Изменение шаблонов трассировки | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- templates [SQL Server], SQL Server Profiler
- Profiler [SQL Server Profiler], templates
- trace templates [SQL Server]
- modifying trace templates
- SQL Server Profiler, templates
ms.assetid: 75b62a54-8d16-4599-bd2d-c42cfcc209f4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ebe8924f46de15a3a34c0f49304c87a904919bdb
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63035045"
---
# <a name="modify-trace-templates"></a>Изменение шаблонов трассировки
  Можно изменить шаблоны, сохраняемые в файле на локальном компьютере, на котором выполняется [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] . Можно также изменить шаблоны, производные от этих файлов. При изменении существующих шаблонов выполняется редактирование таких свойств шаблонов, как классы событий и столбцы данных в том же порядке, в котором эти свойства были установлены первоначально, на вкладке **Выбор событий** диалогового окна **Свойства трассировки** . Классы событий и столбцы данных можно добавлять и удалять, а фильтры изменять. После изменения шаблона создается пользовательский шаблон и исходный системный шаблон остается без изменений. Дополнительные сведения см. в разделе [Сохранение трассировок и шаблонов трассировок](save-traces-and-trace-templates.md).  
  
 Может потребоваться производный шаблон от существующего файла трассировки, если пользователь не помнит (или не сохранил) исходный шаблон, использованный при создании трассировки, или если нужно выполнить ту же трассировку в последующий день. При работе с существующими трассировками можно просматривать свойства, но нельзя изменять их. Чтобы изменить свойства, необходимо остановить или приостановить трассировку. Дополнительные сведения см. в разделах [Создать шаблон на основе файла трассировки или таблицы трассировки (приложение SQL Server Profiler)](sql-server-profiler.md) и [Создать шаблон на основе выполняемой трассировки (приложение SQL Server Profiler)](derive-a-template-from-a-running-trace-sql-server-profiler.md).  
  
 **Создание шаблона трассировки**  
  
 [Создание шаблона трассировки (приложение SQL Server Profiler)](create-a-trace-template-sql-server-profiler.md)  
  
 **Запуск трассировки из шаблона**  
  
 [Создание трассировки (приложение SQL Server Profiler)](create-a-trace-sql-server-profiler.md)  
  
 **Изменение шаблона трассировки**  
  
 [Использование приложения SQL Server Profiler](../../database-engine/modify-a-trace-template-sql-server-profiler.md)  
  
 [Использование Transact-SQL](../../relational-databases/sql-trace/modify-an-existing-trace-transact-sql.md)  
  
 **Добавление и удаление событий из шаблона трассировки или файла трассировки**  
  
 [Использование приложения SQL Server Profiler](specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md)  
  
 [Использование Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
## <a name="see-also"></a>См. также  
 [Запуск трассировки](start-a-trace.md)  
  
  
