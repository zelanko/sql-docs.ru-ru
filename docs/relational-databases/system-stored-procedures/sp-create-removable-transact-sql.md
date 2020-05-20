---
title: sp_create_removable (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_create_removable
- sp_create_removable_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_create_removable
ms.assetid: 06e36ae5-f70d-4a26-9a7f-ee4b9360b355
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 8cef470ba4873a56b21a29d7b2856f58c8ec7b11
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82820573"
---
# <a name="sp_create_removable-transact-sql"></a>sp_create_removable (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Создает базу данных съемных носителей. Создает три или более файлов (один для таблиц системных каталогов, один для журнала транзакций, а также один или более для таблиц данных) и размещает в них базу данных.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Вместо этого рекомендуется использовать [Create Database](../../t-sql/statements/create-database-sql-server-transact-sql.md) .  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_create_removable   
   [ @dbname = ] 'dbname',   
   [ @syslogical= ] 'syslogical',   
   [ @sysphysical = ] 'sysphysical',   
   [ @syssize = ] syssize,   
   [ @loglogical = ] 'loglogical',   
   [ @logphysical = ] 'logphysical',   
   [ @logsize = ] logsize,   
   [ @datalogical1 = ] 'datalogical1',   
   [ @dataphysical1 = ] 'dataphysical1',   
   [ @datasize1 = ] datasize1 ,   
   [ @datalogical16 = ] 'datalogical16',   
   [ @dataphysical16 = ] 'dataphysical16',   
   [ @datasize16 = ] datasize16 ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @dbname = ] 'dbname'`Имя базы данных, создаваемой для использования на съемных носителях. Аргумент *dbname* имеет тип **sysname**.  
  
`[ @syslogical = ] 'syslogical'`Логическое имя файла, содержащего таблицы системных каталогов. *сислогикал* имеет тип **sysname**.  
  
`[ @sysphysical = ] 'sysphysical'`Физическое имя. Включает в себя полный путь к файлу, содержащему таблицы системных каталогов. *сисфисикал* имеет тип **nvarchar (260)**.  
  
`[ @syssize = ] syssize`Размер файла, содержащего таблицы системного каталога, в мегабайтах. *сиссизе* имеет **тип int**. Минимальное значение *сиссизе* — 1.  
  
`[ @loglogical = ] 'loglogical'`Логическое имя файла, содержащего журнал транзакций. *логлогикал* имеет тип **sysname**.  
  
`[ @logphysical = ] 'logphysical'`Физическое имя. Включает в себя полный путь к файлу, содержащему журнал транзакций. *логфисикал* имеет тип **nvarchar (260)**.  
  
`[ @logsize = ] logsize`Размер файла, содержащего журнал транзакций (в мегабайтах). *logsize* имеет **тип int**. Минимальное значение *logsize* — 1.  
  
`[ @datalogical1 = ] 'datalogical'`Логическое имя файла, содержащего таблицы данных. значение *Logic* имеет тип **sysname**.  
  
 Можно создать от 1 до 16 файлов данных. Обычно создание более одного файла данных требуется для больших баз данных, распространяемых на нескольких дисках.  
  
`[ @dataphysical1 = ] 'dataphysical'`Физическое имя. Включает в себя полный путь к файлу, содержащему таблицы данных. *Physical* имеет тип **nvarchar (260)**.  
  
`[ @datasize1 = ] 'datasize'`Размер файла, содержащего таблицы данных, в мегабайтах. *DataSize* имеет **тип int**. Минимальный *Размер* 1.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Remarks  
 Используйте данную хранимую процедуру для создания копий баз данных на таких съемных носителях как компакт-диски, и распространения их среди других пользователей.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение CREATE DATABASE, CREATE ANY DATABASE или ALTER ANY DATABASE.  
  
 В целях сохранения управления над использованием диска в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]разрешение на создание баз данных обычно предоставляется небольшому числу учетных записей входа.  
  
### <a name="permissions-on-data-and-log-files"></a>Разрешения на файлы данных и журналов  
 При выполнении определенных операций в базе данных задаются соответствующие разрешения на ее файлы данных и журнала. Эти разрешения предотвращают случайное повреждение файлов, хранящихся в каталоге с открытыми разрешениями.  
  
|Операция с базой данных|Разрешения, задаваемые для файлов|  
|---------------------------|------------------------------|  
|Изменение для добавления нового файла|Создание|  
|Создание резервной копии|Присоединение|  
|Восстановление|Отсоединен|  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не задает разрешения на файлы данных и файлы журнала.  
  
## <a name="examples"></a>Примеры  
 В ходе выполнения следующего примера создается удаляемая база данных `inventory`.  
  
```  
EXEC sp_create_removable 'inventory',   
   'invsys',  
   'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Data\invsys.mdf'  
, 2,   
   'invlog',  
   'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Data\invlog.ldf', 4,  
   'invdata',  
   'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Data\invdata.ndf',   
10;  
```  
  
## <a name="see-also"></a>См. также  
 [Присоединение и отсоединение базы данных (SQL Server)](../../relational-databases/databases/database-detach-and-attach-sql-server.md)   
 [sp_certify_removable &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-certify-removable-transact-sql.md)   
 [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md)   
 [sp_dbremove &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbremove-transact-sql.md)   
 [sp_detach_db &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-detach-db-transact-sql.md)   
 [sp_helpfile &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpfile-transact-sql.md)   
 [sp_helpfilegroup &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpfilegroup-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
