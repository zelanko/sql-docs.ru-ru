---
title: sp_add_log_file_recover_suspect_db (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_add_log_file_recover_suspect_db_TSQL
- sp_add_log_file_recover_suspect_db
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_log_file_recover_suspect_db
ms.assetid: b41ca3a5-7222-4c22-a012-e66a577a82f6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 52ede21961df29543714f4c31044ef2e261302c0
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85879918"
---
# <a name="sp_add_log_file_recover_suspect_db-transact-sql"></a>sp_add_log_file_recover_suspect_db (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Добавляет файл журнала в файловую группу, если восстановление базы данных не может быть завершено из-за недостатка места для хранения журнала (ошибка 9002). После добавления файла **sp_add_log_file_recover_suspect_db** отключает параметр SUSPECT и завершает восстановление базы данных. Параметры совпадают с параметрами инструкции ALTER DATABASE *database_name* добавления файла журнала.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_add_log_file_recover_suspect_db [ @dbName= ] 'database' ,   
    [ @name = ] 'logical_file_name' ,   
    [ @filename= ] 'os_file_name' ,   
    [ @size = ] 'size' ,   
    [ @maxsize = ] 'max_size' ,   
    [ @filegrowth = ] 'growth_increment'  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @dbName = ] 'database'`Имя базы данных. Аргумент *Database* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @name = ] 'logical_file_name'`Имя, используемое в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при ссылке на файл. Имя должно быть уникальным в пределах сервера. *logical_file_name* имеет тип **nvarchar (260)** и не имеет значения по умолчанию.  
  
`[ @filename = ] 'os_file_name'`Путь и имя файла, используемые операционной системой для файла. Файл должен находиться на сервере, на котором установлен компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)]. *os_file_name* имеет тип **nvarchar (260)** и не имеет значения по умолчанию.  
  
`[ @size = ] 'size_ '`Начальный размер файла. *size* имеет тип **nvarchar (20)** и значение по умолчанию NULL. Укажите целое число (без дробной части). Для указания единицы измерения размера файла (мегабайт или килобайт) можно использовать суффиксы МБ и КБ. По умолчанию — MБ. Минимальное значение размера файла — 512 КБ. Если параметр *size* не указан, по умолчанию используется значение 1 МБ.  
  
`[ @maxsize = ] 'max_size_ '`Максимальный размер, до которого может расти файл. *max_size* имеет тип **nvarchar (20)** и значение по умолчанию NULL. Укажите целое число (без дробной части). Для указания единицы измерения размера файла (мегабайт или килобайт) можно использовать суффиксы МБ и КБ. По умолчанию — MБ.  
  
 Если параметр *max_size* не указан, файл будет расти до тех пор, пока диск не будет заполнен. Журнал приложений [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows предупреждает администратора, если диск заполнен почти полностью.  
  
`[ @filegrowth = ] 'growth_increment_ '`Объем пространства, добавляемого в файл каждый раз, когда требуется новое пространство. *growth_increment* имеет тип **nvarchar (20)** и значение по умолчанию NULL. Значение 0 обозначает отсутствие прироста. Укажите целое число (без дробной части). Значение может быть задано в мегабайтах (МБ), килобайтах (КБ) или процентах (%). Если значение задано в процентах, шаг роста рассчитывается в процентах от размера файла в тот момент, когда потребовалось приращение. Если указано число без суффикса MB, KB или %, то по умолчанию используется MB.  
  
 Если *growth_increment* имеет значение null, значение по умолчанию равно 10%, а значение минимального размера — 64 КБ. Указанный размер округляется до ближайших 64 КБ.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="permissions"></a>Разрешения  
 Разрешения на выполнение по умолчанию имеют члены предопределенной роли сервера **sysadmin** . Эти разрешения не могут передаваться другим пользователям.  
  
## <a name="examples"></a>Примеры  
 В следующем примере база данных `db1` была отмечена во время восстановления как подозрительная из-за недостатка места для хранения журнала (ошибка 9002).  
  
```  
USE master;  
GO  
EXEC sp_add_log_file_recover_suspect_db db1, logfile2,  
'C:\Program Files\Microsoft SQL  
    Server\MSSQL13.MSSQLSERVER\MSSQL\Data\db1_logfile2.ldf',   
    '1MB';  
```  
  
## <a name="see-also"></a>См. также:  
 [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md)   
 [sp_add_data_file_recover_suspect_db &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-data-file-recover-suspect-db-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
