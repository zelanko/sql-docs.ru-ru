---
title: Создание трассировок вручную с помощью хранимых процедур | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: f6f47fa2-7c17-41d4-9f69-9be144d56832
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e2840dced22ccdba8fe71cc87c05d7fd6fb4be58
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85063052"
---
# <a name="create-manual-traces-using-stored-procedures"></a>Создание трассировок вручную с помощью хранимых процедур
  Для создания трассировок на экземпляре компонента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Microsoft [!INCLUDE[tsql](../../includes/tsql-md.md)] предоставляет системные хранимые процедуры на языке [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. Эти системные хранимые процедуры можно использовать для создания трассировок вручную в рамках пользовательских приложений вместо использования приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]. Это позволяет писать пользовательские приложения, отвечающие конкретным нуждам предприятия.  
  
## <a name="in-this-section"></a>в этом разделе  
 В приведенной ниже таблице представлены системные хранимые процедуры, используемые для трассировки экземпляра компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].  
  
|Хранимая процедура|Выполненная задача|  
|----------------------|--------------------|  
|[sys.fn_trace_geteventinfo (Transact-SQL)](/sql/relational-databases/system-functions/sys-fn-trace-geteventinfo-transact-sql)|Возвращает сведения о событии, включенном в трассировку.|  
|[sys.fn_trace_getinfo (Transact-SQL)](/sql/relational-databases/system-functions/sys-fn-trace-getinfo-transact-sql)|Возвращает сведения об указанной трассировке или всех существующих трассировках.|  
|[Хранимая процедура sp_trace_create (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-trace-create-transact-sql)|Создает определение трассировки. Новая трассировка будет находиться в остановленном состоянии.|  
|[Хранимая процедура sp_trace_generateevent (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-trace-generateevent-transact-sql)|Создает пользовательское событие.|  
|[Хранимая процедура sp_trace_setevent (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)|Добавляет класс событий или столбец данных к трассировке либо удаляет их из трассировки.|  
|[Хранимая процедура sp_trace_setstatus (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql)|Запускает, останавливает или закрывает трассировку.|  
|[sys.fn_trace_getfilterinfo (Transact-SQL)](/sql/relational-databases/system-functions/sys-fn-trace-getfilterinfo-transact-sql)|Возвращает сведения о фильтрах, примененных к трассировке.|  
|[sp_trace_setfilter (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql)|Применяет новый или измененный фильтр к трассировке.|  
  
 **Определение пользовательской трассировки при помощи хранимых процедур**  
  
1.  Укажите событие, которое необходимо зарегистрировать с помощью процедуры **sp_trace_setevent**.  
  
2.  Укажите фильтры события. Дополнительные сведения см. в разделе [Создание фильтра трассировки (Transact-SQL)](../../ssms/agent/set-sql-server-alias-for-sql-server-agent-service-ssms.md).  
  
3.  Укажите назначение для данных зарегистрированного события с помощью процедуры **sp_trace_create**.  
  
 Пример использования хранимых процедур трассировки см. в разделе [Создание трассировки (Transact-SQL)](../sql-trace/create-a-trace-transact-sql.md).  
  
 **Установка определения трассировки по умолчанию**  
  
 [Приложение SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
 **Установка параметров по умолчанию для отображения трассировки**  
  
 [Приложение SQL Server Profiler](../../tools/sql-server-profiler/set-trace-display-defaults-sql-server-profiler.md)  
  
 **Создание трассировки**  
  
 [Приложение SQL Server Profiler](../../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md)  
  
 [Transact-SQL](../sql-trace/create-a-trace-transact-sql.md)  
  
 **Добавление или удаление события из шаблона трассировки**  
  
 [Приложение SQL Server Profiler](../../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md)  
  
 [Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  
