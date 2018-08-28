---
title: ALTER EXTERNAL LIBRARY (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/05/2018
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- ALTER EXTERNAL LIBRARY
- ALTER_EXTERNAL_LIBRARY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ALTER EXTERNAL LIBRARY
author: HeidiSteen
ms.author: heidist
manager: cgronlund
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: fd521263853eee1d0c8c25eb135ff2d309eb4a75
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43100822"
---
# <a name="alter-external-library-transact-sql"></a>ALTER EXTERNAL LIBRARY (Transact-SQL)  

[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Изменяет содержимое существующей внешней библиотеки пакетов.

## <a name="syntax"></a>Синтаксис

```text
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

Указывает имя существующей библиотеки пакетов. Область действия библиотек ограничивается пользователем. Имена библиотек должны быть уникальными в контексте определенного пользователя или владельца.

Имя библиотеки не может назначаться произвольным образом. То есть необходимо использовать имя, которое ожидает вызывающая среда выполнения при загрузке пакета.

**owner_name**

Указывает имя пользователя или роли, которой принадлежит внешняя библиотека.

**file_spec**

Указывает содержимое пакета для конкретной платформы. Поддерживается только один файл артефакта на платформу.

Файл можно указать в виде локального или сетевого пути. Если указан параметр источника данных, имя файла может быть относительным путем по отношению к контейнеру, на который ссылается `EXTERNAL DATA SOURCE`.

При необходимости можно указать платформу операционной системы для файла. Для каждой платформы операционной системы для конкретного языка или среды выполнения разрешен только один артефакт файла или содержимое.

**library_bits**

Задает содержимое пакета как шестнадцатеричный литерал, аналогично сборкам. 

Этот параметр можно использовать, если у вас есть необходимое разрешение на изменение библиотеки, но доступ к файлам на сервере ограничен и не удается сохранить содержимое в пути, к которому у сервера есть доступ.

Вместо этого можно передать содержимое пакета в качестве переменной в двоичном формате.

**PLATFORM = WINDOWS**

Указывает платформу для содержимого библиотеки. Это значение является обязательным при изменении существующей библиотеки для добавления другой платформы. Поддерживается только платформа Windows.

## <a name="remarks"></a>Remarks

В языке R пакеты должны быть подготовлены в виде сжатых архивных файлов с расширением ZIP для Windows. В настоящее время поддерживается только платформа Windows.  

Инструкция `ALTER EXTERNAL LIBRARY` только загружает биты библиотеки в базу данных. Измененная библиотека устанавливается при выполнении кода в [sp_execute_external_script (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md), который вызывает библиотеку.

## <a name="permissions"></a>Разрешения

По умолчанию разрешение на запуск ALTER EXTERNAL LIBRARY имеет пользователь **dbo** или любой член роли **db_owner**. Кроме того, внешнюю библиотеку может изменять пользователь, который ее создал.

## <a name="examples"></a>Примеры

В следующем примере изменяется внешняя библиотека `customPackage`.

### <a name="a-replace-the-contents-of-a-library-using-a-file"></a>A. Замена содержимого библиотеки с помощью файла

В следующем примере изменяется внешняя библиотека `customPackage` с помощью сжатого ZIP-файла, содержащего обновленные биты.

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
@script=N'library(customPackage)'
;
```

### <a name="b-alter-an-existing-library-using-a-byte-stream"></a>Б. Изменение существующей библиотеки с помощью байтового потока

В следующем примере существующая библиотека изменяется путем передачи новых битов в виде шестнадцатеричного литерала.

```SQL
ALTER EXTERNAL LIBRARY customLibrary 
SET (CONTENT = 0xabc123) WITH (LANGUAGE = 'R');
```

> [!NOTE]
> В этом примере кода показан только синтаксис. Двоичное значение в `CONTENT =` было усечено для удобства чтения и не создает рабочую библиотеку. Фактическое содержимое двоичной переменной будет гораздо длиннее.

## <a name="see-also"></a>См. также раздел

[CREATE EXTERNAL LIBRARY (Transact-SQL)](create-external-library-transact-sql.md)
[DROP EXTERNAL LIBRARY (Transact-SQL)](drop-external-library-transact-sql.md)  
[sys.external_library_files](../../relational-databases/system-catalog-views/sys-external-library-files-transact-sql.md)  
[sys.external_libraries](../../relational-databases/system-catalog-views/sys-external-libraries-transact-sql.md) 
