---
title: Создание трассировки (приложение SQL Server Profiler) | Документы Microsoft
ms.custom: ''
ms.date: 08/01/2016
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: sql-server-profiler
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- traces [SQL Server], creating
ms.assetid: 0302fa6d-d2b5-43fe-ad70-7a337575b112
caps.latest.revision: 28
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 9b40c4ab9616ec4d7a1271c5e3b5c1a0a36be2e7
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/17/2018
---
# <a name="create-a-trace-sql-server-profiler"></a>создать трассировку (приложение SQL Server Profiler)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] В этом подразделе описывается, как создать трассировку с помощью [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
### <a name="to-create-a-trace"></a>Создание трассировки  
  
1.  В меню **Файл** выберите пункт **Создать трассировку**, а затем подключитесь к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
     отображается диалоговое окно **Свойства трассировки** .  
  
    > **ПРИМЕЧАНИЕ.** Если выбран параметр **Начать трассировку немедленно после установления соединения** , диалоговое окно **Свойства трассировки** не появляется, и начинается трассировка. Чтобы отключить этот параметр, в меню **Сервис** выберите пункт **Параметры** и снимите флажок "Начать трассировку немедленно после установления соединения".  
  
2.  В поле **Имя трассировки** введите имя трассировки.  
  
3.  В списке **Использовать шаблон** выберите шаблон, на котором должна быть основана трассировка, или выберите **Пустой** , если использование шаблона не требуется.  
  
4.  Для сохранения результатов трассировки сделайте следующее.  
  
    -   Нажмите кнопку **Сохранить в файл** для фиксации трассировки в файле. Укажите значение **Установить максимальный размер файла**. Значение по умолчанию — 5 мегабайт.  
  
         При необходимости выберите **Включить операцию переключения на файл продолжения** для автоматического создания новых файлов при достижении максимального размера файла. Также можно дополнительно выбрать **Сервер обрабатывает данные трассировки**, что приведет к тому, что вместо приложения клиента данные трассировки будет обрабатывать служба, выполняющая трассировку. При обработке данных трассировки сервером исключена возможность пропуска события даже в тяжелых условиях, хотя это и приводит к снижению производительности сервера.  
  
    -   Выберите **Сохранить в таблицу** для сохранения результатов трассировки в таблицу базы данных.  
  
         При необходимости установите флажок **Установить максимальное число строк**и укажите значение.  
  
    > **ВНИМАНИЕ!** Если результаты трассировки не сохраняются в файлы или таблицы, их можно просмотреть, пока открыто приложение [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] . Однако результаты трассировки исчезнут после того, как будет остановлена трассировка и закрыто приложение [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]. Чтобы избежать потерю данных трассировки, выберите **Сохранить** в меню **Файл** для сохранения результатов перед закрытием [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
5.  При необходимости установите флажок **Включить время остановки трассировки** и укажите дату и время остановки.  
  
6.  Чтобы добавить или удалить события, столбцы данных или фильтры, перейдите на вкладку **Выбор событий**  . Дополнительные сведения см. в разделе [указать столбцы событий и данных для файла трассировки (приложение SQL Server Profiler)](../../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md).  
  
7.  Чтобы запустить трассировку, нажмите кнопку **Выполнить** .  
  
## <a name="see-also"></a>См. также раздел  
 [Разрешения, необходимые для запуска приложения SQL Server Profiler](../../tools/sql-server-profiler/permissions-required-to-run-sql-server-profiler.md)   
 [Шаблоны и разрешения приложения SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)   
 [Приложение SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)   
 [Сопоставление трассировки с журналом производительности Windows (приложение SQL Server Profiler)](../../tools/sql-server-profiler/correlate-a-trace-with-windows-performance-log-data-sql-server-profiler.md)  
  
  
