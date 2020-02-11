---
title: Шаблоны SQL Server Profiler | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- default SQL Server Profiler templates
- templates [SQL Server], SQL Server Profiler
- Profiler [SQL Server Profiler], templates
- trace templates [SQL Server]
- predefined templates [SQL Server Profiler]
- SQL Server Profiler, templates
ms.assetid: b674e491-dc58-47a1-acdd-7028e9a201fc
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5cac924e926d03dffb9116e5ce7194bb784d45fe
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68186141"
---
# <a name="sql-server-profiler-templates"></a>Шаблоны приложения SQL Server Profiler
  Можно использовать приложение [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] для создания шаблонов, определяющих классы событий и столбцы данных с целью включения в трассировку. После определения и сохранения шаблона можно запустить трассировку, которая будет записывать данные для каждого выбранного класса событий. Шаблоны можно использовать для многих трассировок; сам шаблон не выполняется.  
  
 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]предлагает стандартные шаблоны трассировки, которые позволяют легко настраивать классы событий, которые, скорее всего, понадобятся для определенных трассировок. Например, шаблон «Стандартный» помогает создать общую трассировку для записи входов в систему, выходов из системы, завершенных пакетов и сведений о соединениях. Можно использовать этот шаблон без изменений для выполнения трассировок, либо как начальный вариант с целью создания дополнительных шаблонов с разными конфигурациями событий.  
  
> [!NOTE]  
>  Помимо трассировок из предопределенных шаблонов, приложение [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] позволяет создать трассировки из пустых шаблонов, которые по умолчанию не содержат никаких классов событий. Использование пустого шаблона трассировки полезно, если планируемая трассировка не похожа ни на одну существующую конфигурацию предопределенных шаблонов.  
  
 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]может выполнять трассировку различных типов серверов. Например, можно трассировать [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  Однако классы событий, которые могут быть включены, будут различаться для каждого сервера. Поэтому приложение [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] поддерживает различные шаблоны для различных серверов и делает доступным определенный шаблон, который соответствует выбранному типу сервера.  
  
## <a name="predefined-templates"></a>Предопределенные шаблоны  
 В дополнение к стандартному шаблону (по умолчанию), приложение [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] содержит несколько предопределенных шаблонов для контроля определенных типов событий. В следующей таблице перечисляются предопределенные шаблоны, их назначение, классы событий, для которых они получают сведения.  
  
|Имя шаблона|Назначение шаблона|Классы событий|  
|-------------------|----------------------|-------------------|  
|SP_Counts|Отслеживает поведение при выполнении хранимой процедуры с течением времени.|**SP:Starting**|  
|Standard|Общая начальная точка для создания трассировки. Перехватывает все хранимые процедуры и выполняемые пакеты инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)] . Используется для мониторинга общей активности сервера баз данных.|**Аудит входа в систему**<br /><br /> **Audit Logout**<br /><br /> **ExistingConnection**<br /><br /> **RPC: завершено**<br /><br /> **SQL: BatchCompleted**<br /><br /> **SQL:BatchStarting**|  
|TSQL|Захватывает все инструкции языка [!INCLUDE[tsql](../../includes/tsql-md.md)] , отправленные клиентами на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , и время их отправки. Используется для отладки клиентских приложений.|**Аудит входа в систему**<br /><br /> **Audit Logout**<br /><br /> **ExistingConnection**<br /><br /> **RPC:Starting**<br /><br /> **SQL:BatchStarting**|  
|TSQL_Duration|Захватывает все инструкции языка [!INCLUDE[tsql](../../includes/tsql-md.md)] , отправленные клиентами на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , и время их выполнения (в миллисекундах), и группирует их по длительности. Используется для идентификации медленных запросов.|**RPC: завершено**<br /><br /> **SQL: BatchCompleted**|  
|TSQL_Grouped|Захватывает все инструкции языка [!INCLUDE[tsql](../../includes/tsql-md.md)] , отправленные на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , и время их отправки. Группирует сведения по имени пользователя или клиента, который отправил инструкцию. Используется для изучения запросов от определенного клиента или пользователя.|**Аудит входа в систему**<br /><br /> **Audit Logout**<br /><br /> **ExistingConnection**<br /><br /> **RPC:Starting**<br /><br /> **SQL:BatchStarting**|  
|TSQL_Locks|Захватывает все инструкции языка [!INCLUDE[tsql](../../includes/tsql-md.md)] , переданные клиентами на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , и исключительные события блокировки. Позволяет устранять неполадки с взаимоблокировками, временем истечения ожидания блокировок и событиями укрупнения блокировки.|**Отчет о заблокированном процессе**<br /><br /> **SP: StmtCompleted**<br /><br /> **SP:StmtStarting**<br /><br /> **SQL:StmtCompleted**<br /><br /> **SQL:StmtStarting**<br /><br /> **Deadlock Graph**<br /><br /> **Lock:Cancel**<br /><br /> **Блокировка: взаимоблокировка**<br /><br /> **Lock:Deadlock Chain**<br /><br /> **Блокировка: укрупнение**<br /><br /> **Блокировка: время ожидания (время ожидания>0)**|  
|TSQL_Replay|Захватывает подробные сведения об инструкциях [!INCLUDE[tsql](../../includes/tsql-md.md)] , которые требуются для воспроизведения трассировки. Используется для выполнения последовательной настройки, такой как проверка пропускной способности.|**CursorClose**<br /><br /> **CursorExecute**<br /><br /> **CursorOpen**<br /><br /> **CursorPrepare**<br /><br /> **CursorUnprepare**<br /><br /> **Аудит входа в систему**<br /><br /> **Audit Logout**<br /><br /> **Существующее подключение**<br /><br /> **RPC Output Parameter**<br /><br /> **RPC: завершено**<br /><br /> **RPC:Starting**<br /><br /> **Exec Prepared SQL**<br /><br /> **Prepare SQL**<br /><br /> **SQL: BatchCompleted**<br /><br /> **SQL:BatchStarting**|  
|TSQL_SPs|Захватывает подробные сведения обо всех выполняющихся хранимых процедурах. Используется для анализа составных шагов хранимых процедур. Добавьте событие **SP:Recompile** , если подозреваете, что хранимые процедуры находятся в процессе повторной компиляции.|**Аудит входа в систему**<br /><br /> **Audit Logout**<br /><br /> **ExistingConnection**<br /><br /> **RPC:Starting**<br /><br /> **SP:Completed**<br /><br /> **SP:Starting**<br /><br /> **SP:StmtStarting**<br /><br /> **SQL:BatchStarting**|  
|Настройка|Захватывает сведения о хранимых процедурах и выполнении пакетов инструкций языка [!INCLUDE[tsql](../../includes/tsql-md.md)] . Используется для создания трассировки, которую помощник по настройке компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] может использовать в качестве рабочей нагрузки для настройки баз данных.|**RPC: завершено**<br /><br /> **SP: StmtCompleted**<br /><br /> **SQL: BatchCompleted**|  
  
 Дополнительные сведения о классах событий см. в разделе [SQL Server Event Class Reference](../../relational-databases/event-classes/sql-server-event-class-reference.md).  
  
## <a name="default-template"></a>Шаблон по умолчанию  
 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]автоматически назначает **стандартный** шаблон в качестве шаблона по умолчанию, применяемого к любой новой трассировке. Однако шаблон по умолчанию можно заменить на любой предопределенный шаблон или определенный пользователем шаблон. Чтобы изменить шаблон по умолчанию, установите флажок **Применять как шаблон по умолчанию для выбранного типа сервера** при создании или редактировании шаблона на вкладке **Общие** в диалоговом окне **Свойства шаблона трассировки** .  
  
 Чтобы перейти в диалоговое окно **Свойства шаблона трассировки** , в приложении [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] **Файл** выберите пункт **Шаблоны**и затем выберите пункт **Создать шаблон** или **Изменить шаблон**.  
  
> [!NOTE]  
>  Для каждого типа сервера существует свой шаблон по умолчанию. Изменения шаблона по умолчанию для одного типа сервера не влияет на шаблон по умолчанию для сервера другого типа. Дополнительные сведения о настройке шаблона по умолчанию для определенного типа сервера см. в разделе [Установка значений по умолчанию для определения трассировки (приложение SQL Server Profiler)](set-trace-definition-defaults-sql-server-profiler.md).  
  
## <a name="see-also"></a>См. также:  
 [Создание шаблона трассировки (приложение SQL Server Profiler)](create-a-trace-template-sql-server-profiler.md)   
 [Изменение шаблона трассировки (приложение SQL Server Profiler)](../../database-engine/modify-a-trace-template-sql-server-profiler.md)   
 [Экспорт шаблона трассировки (приложение SQL Server Profiler)](export-a-trace-template-sql-server-profiler.md)   
 [Импорт шаблона трассировки &#40;SQL Server Profiler&#41;](import-a-trace-template-sql-server-profiler.md)  
  
  
