---
title: "Хранимая процедура sp_trace_create (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_trace_create_TSQL
- sp_trace_create
dev_langs: TSQL
helpviewer_keywords: sp_trace_create
ms.assetid: f3a43597-4c5a-4520-bcab-becdbbf81d2e
caps.latest.revision: "38"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: ca00a949b0fe0122f6aba9b8fecfa072374e96f3
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sptracecreate-transact-sql"></a>Хранимая процедура sp_trace_create (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Создает определение трассировки. Новая трассировка будет находиться в остановленном состоянии.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Вместо этого используйте расширенные события.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_trace_create [ @traceid = ] trace_id OUTPUT   
          , [ @options = ] option_value   
          , [ @tracefile = ] 'trace_file'   
     [ , [ @maxfilesize = ] max_file_size ]  
     [ , [ @stoptime = ] 'stop_time' ]  
     [ , [ @filecount = ] 'max_rollover_files' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@traceid=** ] *trace_id*  
 Номер, присвоенный [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для новой трассировки. Любое значение, предложенное пользователем, не будет учитываться. *trace_id* — **int**, значение по умолчанию NULL. Пользователь применяет *trace_id* значение для определения, изменения и управления трассировкой, определенной данной хранимой процедурой.  
  
 [  **@options=** ] *option_value*  
 Указывает набор параметров для трассировки. *option_value* — **int**, не имеет значения по умолчанию. Пользователи могут выбирать сочетания этих параметров путем указания их суммарного значения. Например, чтобы включить оба параметра TRACE_FILE_ROLLOVER и SHUTDOWN_ON_ERROR, указать **6** для *option_value*.  
  
 В следующей таблице содержится список параметров, их значений и описаний.  
  
|Имя параметра|Значение параметра|Description|  
|-----------------|------------------|-----------------|  
|TRACE_FILE_ROLLOVER|**2**|Указывает, что при *max_file_size* достигается текущий трассировочный файл закрывается и создается новый файл. Все новые записи будут сохраняться в новый файл. Новый файл будет иметь то же имя, что и предыдущий, но в конец имени будет добавлено число, показывающее его порядковый номер. Например, если изначально трассировочный файл назывался filename.trc, то следующий трассировочный файл будет называться filename_1.trc, имя следующего трассировочного файла будет filename_2.trc и т. д.<br /><br /> По мере увеличения количества трассировочных файлов число, добавляемое в конец имени файла, будет также последовательно увеличиваться.<br /><br /> SQL Server использует значение по умолчанию *max_file_size* (5 МБ) Если этот параметр указан без указания значения для *max_file_size*.|  
|SHUTDOWN_ON_ERROR|**4**|Указывает, что если трассировка не может быть записана в файл по какой-либо причине, SQL Server останавливается. Этот параметр полезен в случае проведения трассировок по проверке безопасности.|  
|TRACE_PRODUCE_BLACKBOX|**8**|Указывает, что запись последних 5 МБ трассировочных сведений, формируемых сервером, будет сохранена на сервере. Значение параметра TRACE_PRODUCE_BLACKBOX несовместимо со всеми другими.|  
  
 [  **@tracefile=** ] *"**файл_трассировки**"*  
 Указывает расположение и имя файла, в который будет сохраняться трассировка. *файл_трассировки* — **nvarchar(245)** без значения по умолчанию. *файл_трассировки* можно использовать локальный каталог (например, N 'C:\MSSQL\Trace\trace.trc') или UNC-имя общей папки или путь (N'\\\\*Servername*\\*Sharename* \\ *Каталога*\trace.trc').  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]добавит **.trc** расширения ко всем именам файлов трассировки. Если параметр TRACE_FILE_ROLLOVER и *max_file_size* указаны, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] создает новый файл трассировки, если первоначальный файл трассировки увеличивается до максимального размера. Новый файл имеет имя, совпадающее с именем исходного файла, но _ *n*  добавляется для указания последовательности, начиная с **1**. Например, если имя первого трассировочного файла **filename.trc**, второй файл трассировки назывался **filename_1.trc**.  
  
 Если используется параметр TRACE_FILE_ROLLOVER, рекомендуется не использовать в имени исходного файла трассировки символы подчеркивания. Если используются символы подчеркивания, выполняются следующие действия.  
  
-   [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]не выполняет автоматическую нагрузки или предлагает загрузить файлы продолжения (если один из этих параметров смены файла настроены).  
  
-   Функция fn_trace_gettable не загружает файлы продолжения (Если этот параметр указан *number_files* аргумент) которых имя исходного файла трассировки завершается подчеркиванием и числовым значением. (Это не относится к подчеркиваниям и числам, которые автоматически добавляются, когда выполняется переключение на файл продолжения.)  
  
> [!NOTE]  
>  В качестве временного решения в обоих случаях можно переименовать файлы трассировки, исключив подчеркивания из имени исходного файла. Например, если исходный файл имеет имя **my_trace.trc**, а файл продолжения имеет имя **my_trace_1.trc**, можно переименовать файлы **mytrace.trc** и **mytrace_1.trc** перед открытием файла в [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
 *файл_трассировки* не может быть указан при использовании параметра TRACE_PRODUCE_BLACKBOX.  
  
 [  **@maxfilesize=** ] *max_file_size*  
 Указывает максимальный размер файла трассировки в мегабайтах (МБ). *max_file_size* — **bigint**, со значением по умолчанию **5**.  
  
 Если этот параметр указан без параметра TRACE_FILE_ROLLOVER, трассировка остановит запись в файл, когда используемое место на диске превышает сумму, указанную *max_file_size*.  
  
 [  **@stoptime=** ] **"***stop_time***"**  
 Задает дату и время остановки трассировки. *stop_time* — **datetime**, значение по умолчанию NULL. Если указано значение NULL, трассировка будет работать до тех пор, пока не будет остановлена вручную или пока не остановится сервер.  
  
 Если оба *stop_time* и *max_file_size* указаны, а параметр TRACE_FILE_ROLLOVER не указан, трассировка остановится при достижении максимального размера файла или указанное время. Если *stop_time*, *max_file_size*и параметр TRACE_FILE_ROLLOVER, трассировка остановится в указанное время, при условии, что трассировка не заполнения диска.  
  
 [  **@filecount=** ] **"***max_rollover_files***"**  
 Указывает максимальное количество файлов трассировки, образованных с одним базовым именем. *max_rollover_files* — **int**, превышающим единицу. Этот аргумент имеет смысл только в случае, если указан параметр TRACE_FILE_ROLLOVER. Когда *max_rollover_files* указано, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] пытается поддерживать не более чем *max_rollover_files* файлы трассировки, удаляя самые старые файлы перед открытием файла трассировки. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] отслеживает возраст файлов трассировки, добавляя число в конец базового имени файла.  
  
 Например, если *файл_трассировки* параметр определен как «c:\mytrace», файл с именем «c:\mytrace_123.trc» старее, чем файл с именем «c:\mytrace_124.trc». Если *max_rollover_files* установлен в значение 2, то SQL Server удаляет файл «c:\mytrace_123.trc» перед созданием трассировочного файла «c:\mytrace_125.trc».  
  
 Обратите внимание, что [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] пытается удалить файл только один раз и не может удалить файл, используемый другим процессом. Поэтому, если другое приложение работает с файлами трассировки во время трассировки, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может оставить эти файлы в файловой системе.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 В следующей таблице описаны значения кодов, которые могут быть возвращены пользователю при завершении хранимой процедуры.  
  
|Код возврата|Description|  
|-----------------|-----------------|  
|0|Нет ошибки.|  
|1|Неизвестная ошибка.|  
|10|Недопустимые параметры. Возвращается, если указанные параметры несовместимы.|  
|12|Файл не создан.|  
|13|Нехватка памяти. Возвращается, когда для выполнения указанного действия недостаточно памяти.|  
|14|Недопустимое время останова. Возвращается, если указанное время останова уже прошло.|  
|15|Недопустимые аргументы. Возвращается, если пользователь ввел несовместимые аргументы.|  
  
## <a name="remarks"></a>Замечания  
 **Хранимая процедура sp_trace_create** — [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] хранимую процедуру, которая выполняет многие действия, ранее выполнявшиеся **xp_trace_\***  расширенные хранимые процедуры в более ранних версиях SQL Server. Используйте **sp_trace_create** вместо:  
  
-   **xp_trace_addnewqueue**  
  
-   **xp_trace_setqueuecreateinfo**  
  
-   **xp_trace_setqueuedestination**  
  
 **Хранимая процедура sp_trace_create** только создает определение трассировки. Эта хранимая процедура не может быть использована для запуска или изменения трассировки.  
  
 Параметры всех трассировки SQL хранимые процедуры (**sp_trace_xx**) жестко типизированы. Если эти аргументы указываются с неправильными типами данных входных параметров, как указано в описании их аргументов, хранимая процедура возвратит ошибку.  
  
 Для **sp_trace_create**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] учетная запись службы должна иметь разрешение на запись в папку с файлами трассировки. Если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] учетная запись службы не имеет прав администратора на компьютере, где находится файл трассировки, необходимо явно предоставить разрешение на запись в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] учетной записи службы.  
  
> [!NOTE]  
>  Можно автоматически загружать файл трассировки, созданных с помощью **sp_trace_create** в таблицу с помощью **fn_trace_gettable** системная функция. Сведения об использовании этой системной функции см. в разделе [sys.fn_trace_gettable &#40; Transact-SQL &#41; ](../../relational-databases/system-functions/sys-fn-trace-gettable-transact-sql.md).  
  
 Пример использования хранимых процедур трассировки см. в разделе [Создание трассировки (Transact-SQL)](../../relational-databases/sql-trace/create-a-trace-transact-sql.md).  
  
 **TRACE_PRODUCE_BLACKBOX** имеет следующие характеристики:  
  
-   Это продолжение трассировки. Значение по умолчанию *file_count* равно 2, но может быть переопределено с помощью пользователя *filecount* параметр.  
  
-   Значение по умолчанию *file_size* как и для других трассировок составляет 5 МБ и может быть изменено.  
  
-   Не удалось задать имя файла. Файл будет сохранен как: **N'%SQLDIR%\MSSQL\DATA\blackbox.trc "**  
  
-   В трассировке будут содержаться только следующие события и их столбцы.  
  
    -   **Запуск RPC**  
  
    -   **Начало пакета**  
  
    -   **Исключение**  
  
    -   **Внимание**  
  
-   События или столбцы нельзя добавить или удалить из данной трассировки.  
  
-   Для данной трассировки нельзя указать фильтры.  
  
## <a name="permissions"></a>Permissions  
 Пользователь должен иметь разрешение ALTER TRACE.  
  
## <a name="see-also"></a>См. также:  
 [Хранимая процедура sp_trace_generateevent &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-trace-generateevent-transact-sql.md)   
 [Хранимая процедура sp_trace_setevent (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [sp_trace_setfilter (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql.md)   
 [Хранимая процедура sp_trace_setstatus (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql.md)   
 [Трассировка SQL](../../relational-databases/sql-trace/sql-trace.md)  
  
  
