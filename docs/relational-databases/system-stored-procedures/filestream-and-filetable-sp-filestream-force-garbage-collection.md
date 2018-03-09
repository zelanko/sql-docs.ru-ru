---
title: "sp_filestream_force_garbage_collection (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/22/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_filestream_force_garbage_collection
- sp_filestream_force_garbage_collection_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- FILESTREAM [SQL Server]
- sp_filestream_force_garbage_collection
ms.assetid: 9d1efde6-8fa4-42ac-80e5-37456ffebd0b
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d424bb470ac9da5edc6b314e62ffaa2e1e72b923
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="filestream-and-filetable---spfilestreamforcegarbagecollection"></a>FileStream и FileTable - sp_filestream_force_garbage_collection
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Принудительно запускает сборщик мусора FILESTREAM, который удаляет все ненужные файлы FILESTREAM.  
  
 Контейнер FILESTREAM не может быть удален до тех пор, пока все удаленные файлы в нем не будут очищены сборщиком мусора. Сборщик мусора FILESTREAM запускается автоматически. Тем не менее при необходимости удалить контейнер, прежде чем сборщик мусора был запущен, можно использовать sp_filestream_force_garbage_collection вручную запустить сборщик мусора.  
  
  
## <a name="syntax"></a>Синтаксис  
  
```  
sp_filestream_force_garbage_collection  
    [ @dbname = ]  'database_name',  
    [ @filename = ] 'logical_file_name' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 **@dbname** = *database_name***'**  
 Обозначает имя базы данных, в которой будет запущен сборщик мусора.  
  
> [!NOTE]  
>  *DBName* — **sysname**. Если он не указан, предполагается текущая база данных.  
  
 **@filename** = *logical_file_name*  
 Обозначает логическое имя контейнера FILESTREAM, в котором будет запущен сборщик мусора. **@filename**является необязательным. Если логическое имя файла не указан, сборщик мусора освобождает все контейнеры FILESTREAM в указанной базе данных.  
  
## <a name="return-code-values"></a>Значения кода возврата  
  
|||  
|-|-|  
|Значение|Описание|  
|0|Операция выполнена успешно|  
|1|Ошибка при выполнении операции|  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Значение|Описание|  
|-----------|-----------------|  
|*file_name*|Указывает имя контейнера FILESTREAM|  
|*num_collected_items*|Указывает число элементов FILESTREAM (файлов и каталогов), которые были собраны как мусор (удалены) в данном контейнере.|  
|*num_marked_for_collection_items*|Указывает число элементов FILESTREAM (файлов и каталогов), которые были отмечены для сборки мусора в данном контейнере. Эти элементы еще не были удалены, но могут оказаться пригодными для удаления после фазы сборкой мусора.|  
|*num_unprocessed_items*|Указывает число подлежащих сборке мусора элементов FILESTREAM (файлов и каталогов), для которых сборка в данном контейнере не была выполнена. Это может произойти по разным причинам, включая следующие.<br /><br /> Файлы закреплены, так как еще не создана резервная копия журналов или контрольной точки.<br /><br /> Файлы относятся к модели восстановления FULL или BULK_LOGGED.<br /><br /> Существует длительно выполняющаяся активная транзакция.<br /><br /> Задание чтения журнала репликации не выполнена. См. в техническом документе [хранилище FILESTREAM в SQL Server 2008](http://go.microsoft.com/fwlink/?LinkId=209156) для получения дополнительной информации.|  
|*last_collected_xact_seqno*|Возвращает последний соответствующий номер последовательности LSN, до которого для файлов была выполнена сборка мусора в указанном контейнере FILESTREAM.|  
  
## <a name="remarks"></a>Remarks  
 Явным образом запускает задачу сборщика мусора FILESTREAM для указанной базы данных (и контейнера FILESTREAM). Файлы, которые больше не требуются, удаляются процессом сборки мусора. Время, необходимое на выполнение этой операции, зависит от объема данных FILESTREAM в базе данных или контейнере, а также от объема операций DML, произведенных в последнее время над данными FILESTREAM. Хотя эта операция может выполняться и при режиме работы базы данных в сети, но в таком случае производительность базы данных может понизиться, так как во время сборки мусора выполняются различные операции ввода-вывода.  
  
> [!NOTE]  
>  Рекомендуется запускать эту операцию только при необходимости и в нерабочее время.  
  
Несколько вызовов этой хранимой процедуры можно осуществить одновременно только в различных контейнерах или базах данных.  

Из-за операций двухэтапной хранимую процедуру следует запускать дважды, чтобы фактически удалить базовых файлов Filestream.  

Сбора мусора (GC) полагается на усечение журнала. Таким образом Если файлы были удалены недавно, на использование модели полного восстановления базы данных, они являются GC-ed только после того, будет переведена в резервной копии журнала из этих частей журнала транзакций и часть журнала помечена как неактивная. В базе данных с использованием простой модели восстановления, происходит усечение журнала после `CHECKPOINT` была выполнена в базе данных.  


## <a name="permissions"></a>Разрешения  
 Требуется членство в роли базы данных db_owner.  
  
## <a name="examples"></a>Примеры  
 В следующих примерах сборщик мусора запускается для контейнеров FILESTREAM в базе данных `FSDB`.  
  
### <a name="a-specifying-no-container"></a>A. Без указания контейнера  
  
```sql  
USE FSDB;  
GO  
EXEC sp_filestream_force_garbage_collection @dbname = N'FSDB';  
```  
  
### <a name="b-specifying-a-container"></a>Б. С указанием контейнера  
  
```sql  
USE FSDB;  
GO  
EXEC sp_filestream_force_garbage_collection @dbname = N'FSDB',
    @filename = N'FSContainer';  
```  
  
## <a name="see-also"></a>См. также  
 [Хранилище FILESTREAM в SQL Server 2008](http://go.microsoft.com/fwlink/?LinkId=209156)  
  
  
