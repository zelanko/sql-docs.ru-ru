---
title: Трассировка и воспроизведение событий | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- replaying events
- traces [SMO]
- events [SMO], replaying
- events [SMO], tracing
ms.assetid: f41b3f85-2f6c-4c3e-9776-8c73d2cc7a53
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 7b40ddaddc652f5b5e37fc23b1330ebd8f92c475
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47753836"
---
# <a name="tracing-and-replaying-events"></a>Трассировка и воспроизведение событий
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  В SMO **трассировки** и **воспроизведения** объекты в <xref:Microsoft.SqlServer.Management.Trace> пространства имен предоставляют программный доступ к [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] функциональность, которая используется для наблюдения за экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]или [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Приложение позволяет собирать и сохранять данные о каждом событии в файле или в таблице для последующего анализа. Например, с помощью приложения можно наблюдать за рабочей средой, чтобы определить, какие процедуры сказываются на производительности из-за того, что выполняются слишком медленно.  
  
 **Трассировки** и **воспроизведения** объекты предоставляют набор объектов, которые могут использоваться для создания трассировок экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Эти объекты можно использовать из пользовательских приложений для создания вручную трассировок для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] или служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Кроме того, SMO **трассировки** объекты могут использоваться для чтения файлов трассировок SQL и таблиц, которые были созданы при наблюдении за [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], службами or DTS logging.  
  
 Объекты **Trace** SMO позволяют выполнять следующие функции:  
  
-   создать трассировку;  
  
-   назначить фильтры для трассировки;  
  
-   назначить отслеживаемые события;  
  
-   остановить и запустить трассировку;  
  
-   прочитать файлы трассировки и таблицы трассировки;  
  
-   получить сведения о событиях трассировки;  
  
-   получить сведения о фильтрах трассировки;  
  
-   программно управлять данными трассировки;  
  
-   записать файлы и таблицы трассировки;  
  
-   воспроизвести файлы и таблицы трассировки.  
  
 Данные трассировки из **трассировки** и **воспроизведения** можно использовать объекты SMO-приложении или исследовать их вручную с помощью [SQL Server Profiler](../../../tools/sql-server-profiler/sql-server-profiler.md). Данные трассировки также совместимы с [трассировки SQL](../../../relational-databases/sql-trace/sql-trace.md) хранимые процедуры, которые также обеспечивают возможности трассировки.  
  
 Объекты трассировки SMO находятся в пространстве имен <xref:Microsoft.SqlServer.Management.Trace>, для использования которого необходима ссылка на файл Microsoft.SQLServer.ConnectionInfo.dll.  
  
 **Трассировки** и **воспроизведения** объектов требуется [ServerConnection](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.serverconnection.aspx) <xref:Microsoft.SqlServer.Management.Smo.Server.%23ctor%2A> объектов для установления соединения с экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. [ServerConnection](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.serverconnection.aspx) объект находится в [Microsoft.SqlServer.Management.Common](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common) пространство имен, которое требуется ссылка на файл Microsoft.SQLServer.ConnectionInfo.dll.  
  
> [!NOTE]  
>  Объекты **Trace** и **Replay** не поддерживаются в 64-разрядной версии платформы.  
  
  
