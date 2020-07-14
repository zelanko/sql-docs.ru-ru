---
title: Параметр конфигурации сервера "optimize for ad hoc workloads" | Документы Майкрософт
description: Изучите параметр optimize for ad hoc workloads. Используйте его для повышения эффективности кеширования планов рабочих нагрузок SQL Server, содержащих много отдельных нерегламентированных пакетов.
ms.custom: ''
ms.date: 11/17/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- optimize for ad hoc workloads option
ms.assetid: 0972e028-3a8e-454b-a186-e814a1d431f2
author: markingmyname
ms.author: maghan
ms.openlocfilehash: d93df848459f003fa4e2c2be0b88ddd9973422c5
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85781851"
---
# <a name="optimize-for-ad-hoc-workloads-server-configuration-option"></a>Параметр конфигурации сервера «optimize for ad hoc workloads»
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Параметр **optimize for ad hoc workloads** используется для повышения эффективности кэширования планов рабочих нагрузок, содержащих много отдельных нерегламентированных пакетов. Если этот параметр имеет значение 1, компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] при первой компиляции пакета сохраняет в кэше планов небольшую скомпилированную заглушку плана, а не полный откомпилированный план. Это несколько снижает требования к памяти, так как кэш планов не заполняется скомпилированными, не используемыми повторно планами. 
  
  Откомпилированная заглушка плана позволяет компоненту [!INCLUDE[ssDE](../../includes/ssde-md.md)] понять, что данный нерегламентированный пакет компилировался ранее, но от него сохранилась только заглушка. При повторном вызове этого пакета для компиляции или выполнения компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] откомпилирует пакет, удалит из кэша планов откомпилированную заглушку плана и добавит туда полный скомпилированный план. 
  
 Скомпилированная заглушка плана принадлежит к объектам cacheobjtypes, которые можно просмотреть в представлении каталога sys.dm_exec_cached_plans. У каждой заглушки есть уникальный дескриптор SQL и дескриптор плана. Со скомпилированной заглушкой плана не связан план выполнения. Запрос по дескриптору плана не вернет XML-код Showplan.  
  
 [Флаг трассировки 8032](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) восстанавливает параметры предела кэша до значения в RTM-версии [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], что обычно позволяет увеличить размер кэша. Используйте этот параметр, если часто используемые повторно записи кэша не помещаются в кэш и параметру конфигурации сервера "Оптимизировать для нерегламентированной рабочей нагрузки" не удалось разрешить эту проблему с помощью кэша планов.  
  
> [!WARNING]  
>  Применение флага трассировки 8032 может привести к снижению производительности, если увеличение кэша приводит к уменьшению объема памяти, доступной для других потребителей памяти, например для буферного пула.  

## <a name="recommendations"></a>Рекомендации
Старайтесь, чтобы в кэше планов не находилось много планов разового применения. Такая проблема часто возникает при несогласованных определениях типов данных параметров запроса. Это относится в первую очередь к длине строк, но может случаться с любыми типами данных, имеющими максимальную длину, точность или масштаб. Например, если параметр с именем @Greeting передается как nvarchar(10) в одном вызове и как nvarchar(20) в следующем вызове, для каждого размера параметра создаются отдельные планы. Если в запросе есть несколько параметров и они определяются при вызове несогласованно, может существовать большое количество планов запросов для каждого запроса. Для каждого сочетания используемых длин и типов данных параметров запроса могут иметься отдельные планы.

Если количество одноразовых планов занимает существенную часть памяти [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] на сервере OLTP и эти планы являются нерегламентированными, используйте этот параметр сервера для уменьшения объема используемой этими объектами памяти.
Чтобы найти количество одноразовых кэшированных планов, выполните следующий запрос:

```sql
SELECT objtype, cacheobjtype, 
  AVG(usecounts) AS Avg_UseCount, 
  SUM(refcounts) AS AllRefObjects, 
  SUM(CAST(size_in_bytes AS bigint))/1024/1024 AS Size_MB
FROM sys.dm_exec_cached_plans
WHERE objtype = 'Adhoc' AND usecounts = 1
GROUP BY objtype, cacheobjtype;
```

> [!IMPORTANT]
> Когда параметру **optimize for ad hoc workloads** присваивается значение 1, это влияет только на новые планы; те планы, которые уже находятся в кэше планов, остаются неизменными.
> Чтобы немедленно применить параметр к уже кэшированным планам запросов, необходимо очистить кэш планов с помощью инструкции [ALTER DATABASE SCOPED CONFIGURATION CLEAR PROCEDURE_CACHE](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md) или перезапустить [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

## <a name="see-also"></a>См. также:  
 [sys.dm_exec_cached_plans (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md)   
 [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
  
