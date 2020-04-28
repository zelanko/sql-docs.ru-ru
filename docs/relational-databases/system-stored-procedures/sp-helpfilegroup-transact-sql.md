---
title: sp_helpfilegroup (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helpfilegroup_TSQL
- sp_helpfilegroup
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpfilegroup
ms.assetid: 619716b5-95dc-4538-82ae-4b90b9da8ebc
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6fe9798b6a9f560621eba9806e25081f72e316c8
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68122537"
---
# <a name="sp_helpfilegroup-transact-sql"></a>sp_helpfilegroup (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает имена и атрибуты файловых групп, связанных с текущей базой данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helpfilegroup [ [ @filegroupname = ] 'name' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @filegroupname = ] 'name'`Логическое имя любой файловой группы в текущей базе данных. Аргумент *Name* имеет тип **sysname**и значение по умолчанию NULL. Если параметр *Name* не указан, отображаются все файловые группы в текущей базе данных, и отображается только первый результирующий набор, отображаемый в разделе результирующие наборы.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**Группа**|**sysname**|Имя файловой группы.|  
|**Идентификатор**|**smallint**|Числовой идентификатор файловой группы.|  
|**filecount**|**int**|Количество файлов в файловой группе.|  
  
 Если указано *имя* , возвращается по одной строке для каждого файла в файловой группе.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**file_in_group**|**sysname**|Логическое имя файла в файловой группе.|  
|**ИД**|**smallint**|Числовой идентификатор файла.|  
|**файлов**|**nchar (260)**|Физическое имя, включающее путь к каталогу.|  
|**size**|**nvarchar (15)**|Размер файла в килобайтах.|  
|**MAXSIZE**|**nvarchar (15)**|Максимальный размер файла.<br /><br /> Максимальный размер, до которого может вырасти файл. Значение UNLIMITED в этом поле означает, что файл может расти, пока диск не будет заполнен.|  
|**growth**|**nvarchar (15)**|Значение прироста размера файла. Параметр задает объем пространства, добавляемого к файлу каждый раз, когда требуется дополнительное пространство.<br /><br /> 0 = файл имеет фиксированный размер и не может расти.|  
  
## <a name="permissions"></a>Разрешения  
 Необходимо быть членом роли **public**.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-returning-all-filegroups-in-a-database"></a>A. Возвращать все файловые группы в базе данных  
 В приведенном ниже примере возвращаются сведения о файловых группах в образце базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC sp_helpfilegroup;  
GO  
```  
  
### <a name="b-returning-all-files-in-a-filegroup"></a>Б) Возвращать все файлы в файловой группе  
 В приведенном ниже примере возвращаются сведения обо всех файлах файловой группы `PRIMARY` в образце базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC sp_helpfilegroup 'PRIMARY';  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Ядро СУБД хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [sp_helpfile &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpfile-transact-sql.md)   
 [sys. database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [sys. master_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)   
 [sys. FILEGROUP &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md)   
 [Системные хранимые процедуры &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Файлы и файловые группы базы данных](../../relational-databases/databases/database-files-and-filegroups.md)  
  
  
