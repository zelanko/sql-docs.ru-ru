---
title: "ALTER ВНЕШНЕЙ БИБЛИОТЕКИ (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 10/05/2017
ms.prod: sql-non-specified
ms.prod_service: 
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER EXTERNAL LIBRARY
- ALTER_EXTERNAL_LIBRARY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ALTER EXTERNAL LIBRARY
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 29122bdf543e82c1f429cf401b5fe1d8383515fc
ms.openlocfilehash: b728fa43959ee047173b1533e70d46e5b1e0f7c1
ms.contentlocale: ru-ru
ms.lasthandoff: 10/10/2017

---
# <a name="alter-external-library-transact-sql"></a>ALTER ВНЕШНЕЙ БИБЛИОТЕКИ (Transact-SQL)  

[!INCLUDE[tsql-appliesto-ssvnxt-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssvnxt-xxxx-xxxx-xxx.md)]

Изменяет содержимое существующего пакета, внешние библиотеки.

## <a name="syntax"></a>Синтаксис

```
ALTER EXTERNAL LIBRARY library_name
[ AUTHORIZATION owner_name ]
SET <file_spec>
WITH ( LANGUAGE = 'R' )
[ ; ]

<file_spec> ::=
{
(CONTENT = { <client_library_specifier> | <library_bits> | NONE}
[, PLATFORM = WINDOWS )
}

<client_library_specifier> :: =
  '[\\computer_name\]share_name\[path\]manifest_file_name'
| '[local_path\]manifest_file_name'
| '<relative_path_in_external_data_source>'

<library_bits> :: =
{ varbinary_literal | varbinary_expression }
```

### <a name="arguments"></a>Аргументы

**library_name**

Указывает имя существующей библиотеки пакета. Библиотеки областью действия пользователя. То есть имена библиотек, считаются уникальными в контексте определенного пользователя или владелец.

**owner_name**

Указывает имя пользователя или роли, которой принадлежит внешней библиотеки.

**file_spec**

Указывает содержимое пакета для конкретной платформы. Поддерживается только один файл артефакта каждой платформы.

Файл можно указать в виде локальной или сетевой путь. Если указан параметр источника данных, имя файла может быть относительным по отношению к контейнеру, на которые ссылается `EXTERNAL DATA SOURCE`.

При необходимости можно указать платформу операционной системы для файла. Для каждой платформы операционной системы для конкретного языка или среды выполнения разрешена артефакта только один файл или содержимое.

**Источник_данных = external_data_source_name**

Задает имя внешнего источника данных, содержащий местоположение файла библиотеки. Это расположение должно указывать путь к хранилищу BLOB-объектов Azure. Для создания внешнего источника данных, используйте [CREATE EXTERNAL DATA SOURCE (Transact-SQL)](create-external-data-source-transact-sql.md).

> [!IMPORTANT] 
> В настоящее время больших двоичных объектов не поддерживаются как источник данных в выпуске 2017 г. SQL Server.

**library_bits**

Задает содержимое пакета как Шестнадцатеричный литерал, аналогично сборки. Этот параметр позволяет пользователям создавать библиотеки для изменения библиотеки, если они имеют необходимое разрешение, но не имеют доступ к пути файла в папку, для которой у сервера есть доступ.

**ПЛАТФОРМА = WINDOWS**

Указывает платформу для библиотеки содержимого. Это значение является обязательным при изменении существующей библиотеки для добавления другой платформе. Windows является единственным поддерживаемой платформы.

## <a name="remarks"></a>Замечания

Для языка R, пакеты необходимо подготовить в виде файлов ZIP-архив. ПОЧТОВЫЙ модуль для Windows. В настоящее время поддерживается только на платформу Windows.  

`ALTER EXTERNAL LIBRARY` Инструкции только отправляет биты библиотеки в базе данных. Изменения библиотеки фактически не устанавливается, пока пользователь запускает внешнего скрипта после него, выполнив [sp_execute_external_script (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).

## <a name="permissions"></a>Permissions

Требуется `ALTER ANY EXTERNAL LIBRARY` разрешение. Пользователей, создавших внешней библиотеки, можно изменить, внешние библиотеки.

## <a name="examples"></a>Примеры

Следующие примеры изменяет вызывается customPackage внешней библиотеки.

### <a name="a-replace-the-contents-of-a-library-using-a-file"></a>A. Замените содержимое библиотеки с помощью файла

В следующем примере изменяется внешней библиотеки вызывается customPackage, с помощью ZIP-файл, содержащий обновленные bits.

```sql
ALTER EXTERNAL LIBRARY customPackage 
SET 
  (CONTENT = 'C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\customPackage.zip')
WITH (LANGUAGE = 'R');
```  

Чтобы установить обновленную библиотеку, выполните хранимую процедуру `sp_execute_external_script`.

```sql   
EXEC sp_execute_external_script 
@language =N'R', 
@script=N'
# load customPackage
library(customPackage)
# call customPackageFunc
OutputDataSet <- customPackageFunc()
'
WITH RESULT SETS (([result] int));
```

### <a name="b-alter-an-existing-library-using-a-byte-stream"></a>Б. Изменить существующую библиотеку с помощью байтового потока

В следующем примере изменяется существующую библиотеку, передавая новых битов как шестнадцатеричная литерала.

```SQL
ALTER EXTERNAL LIBRARY customLibrary FROM (CONTENT = 0xabc123) WITH (LANGUAGE = 'R');
```

## <a name="see-also"></a>См. также:  

[Создание ВНЕШНЕЙ БИБЛИОТЕКИ (Transact-SQL)](create-external-library-transact-sql.md)
[DROP ВНЕШНЕЙ БИБЛИОТЕКИ (Transact-SQL)](drop-external-library-transact-sql.md)  
[sys.external_library_files](../../relational-databases/system-catalog-views/sys-external-library-files-transact-sql.md)  
[sys.external_libraries](../../relational-databases/system-catalog-views/sys-external-libraries-transact-sql.md)  

