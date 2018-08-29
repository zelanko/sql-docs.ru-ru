---
title: sp_add_data_file_recover_suspect_db (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_add_data_file_recover_suspect_db
- sp_add_data_file_recover_suspect_db_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_data_file_recover_suspect_db
ms.assetid: b25262aa-a228-48b7-8739-6581c760b171
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d6d2facde85a46db3c54d3d94e7502e6341ae57a
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43021703"
---
# <a name="spadddatafilerecoversuspectdb-transact-sql"></a>sp_add_data_file_recover_suspect_db (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Добавляет файл данных в файловую группу, если восстановление базы данных не может быть завершено из-за недостатка места в файловой группе (ошибка 1105). После добавления файла эта хранимая процедура отключает параметр подозрения и завершает восстановление базы данных. Параметры такие же, как у инструкции ALTER DATABASE *имя_базы_данных* ADD FILE.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_add_data_file_recover_suspect_db [ @dbName= ] 'database'   
    , [ @filegroup = ] 'filegroup_name'   
    , [ @name = ] 'logical_file_name'   
    , [ @filename= ] 'os_file_name'   
    , [ @size = ] 'size'   
    , [ @maxsize = ] 'max_size'   
    , [ @filegrowth = ] 'growth_increment'  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@dbName=** ] **"*** базы данных* **"**  
 Имя базы данных. *База данных* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@filegroup=** ] **"*** filegroup_name* **"**  
 Файловая группа, в которую будет добавлен файл. *filegroup_name* — **nvarchar(260)**, значение по умолчанию NULL, который соответствует первичному файлу.  
  
 [  **@name=** ] **"*** логическое_имя_файла* **"**  
 Имя, используемое компонентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для ссылки на файл. Имя должно быть уникальным в пределах сервера. *логическое_имя_файла* — **nvarchar(260)**, не имеет значения по умолчанию.  
  
 [ **@filename=** ] **'***os_file_name* **'**  
 Путь и имя файла, используемые операционной системой. Файл должен находиться на сервере, на котором установлен экземпляр компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)]. *имя_файла_ос* — **nvarchar(260)**, не имеет значения по умолчанию.  
  
 [  **@size=** ] **"*** размер* **"**  
 Задает начальный размер файла. *размер* — **nvarchar(20)**, значение по умолчанию NULL. Укажите целое число (без дробной части). Для указания единицы измерения размера файла (мегабайт или килобайт) можно использовать суффиксы МБ и КБ. По умолчанию — MБ. Минимальное значение размера файла — 512 КБ. Если *размер* не указан, значение по умолчанию составляет 1 МБ.  
  
 [  **@maxsize=** ] **"*** max_size* **"**  
 Максимальный размер, до которого может увеличиться размер файла. *max_size* — **nvarchar(20)**, значение по умолчанию NULL. Укажите целое число (без дробной части). Для указания единицы измерения размера файла (мегабайт или килобайт) можно использовать суффиксы МБ и КБ. По умолчанию — MБ.  
  
 Если *max_size* не указан, файл будет увеличиваться до заполнения диска. Журнал приложений [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows предупреждает администратора, если диск заполнен почти полностью.  
  
 [  **@filegrowth=** ] **"*** growth_increment* **"**  
 Объем пространства, добавляемого к файлу каждый раз, когда требуется новое пространство. *growth_increment* — **nvarchar(20)**, значение по умолчанию NULL. Значение 0 обозначает отсутствие прироста. Укажите целое число (без дробной части). Значение может быть задано в мегабайтах (МБ), килобайтах (КБ) или процентах (%). Если значение задано в процентах, шаг роста рассчитывается в процентах от размера файла в тот момент, когда потребовалось приращение. Если указано число без суффикса MB, KB или %, то по умолчанию используется MB.  
  
 Если *growth_increment* имеет значение NULL, значение по умолчанию — 10% и минимальное значение — 64 КБ. Указанный размер округляется до ближайших 64 КБ.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="permissions"></a>Разрешения  
 Выполнение разрешения назначаются по умолчанию членам **sysadmin** предопределенной роли сервера. Эти разрешения не могут передаваться другим пользователям.  
  
## <a name="examples"></a>Примеры  
 В следующем примере база данных `db1` была отмечена во время восстановления как подозрительная из-за недостатка места в файловой группе `fg1` (ошибка 1105).  
  
```  
USE master;  
GO  
EXEC sp_add_data_file_recover_suspect_db db1, fg1, file2,  
    'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Data\db1_file2.mdf', '1MB';  
```  
  
## <a name="see-also"></a>См. также  
 [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md)   
 [sp_add_log_file_recover_suspect_db &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-log-file-recover-suspect-db-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
