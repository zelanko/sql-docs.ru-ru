---
title: CREATE EXTERNAL LIBRARY (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/05/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- CREATE EXTERNAL LIBRARY
- CREATE_EXTERNAL_LIBRARY_TSQL
- EXTERNAL LIBRARY
- EXTERNAL_LIBRARY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CREATE EXTERNAL LIBRARY
author: HeidiSteen
ms.author: heidist
manager: cgronlund
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d8c6b8ea4467ddc09a08d21a337b1b5c8c44f34e
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/28/2018
ms.locfileid: "52538805"
---
# <a name="create-external-library-transact-sql"></a>CREATE EXTERNAL LIBRARY (Transact-SQL)  

[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]  

Отправляет пакеты R в базу данных из указанного байтового потока или пути к файлу.

Эта инструкция служит универсальным механизмом для администратора базы данных, с помощью которого он может отправлять артефакты, необходимые для любой новой внешней языковой среды выполнения (R, Python, Java и т. д.) и платформы операционной системы, поддерживаемой [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)]. 

В настоящее время поддерживаются только язык R и платформа Windows. Поддержка Python и Linux планируется в будущих выпусках.

## <a name="syntax"></a>Синтаксис

```text
CREATE EXTERNAL LIBRARY library_name  
    [ AUTHORIZATION owner_name ]  
FROM <file_spec> [,...2]  
WITH ( LANGUAGE = 'R' )  
[ ; ]  

<file_spec> ::=  
{  
(CONTENT = { <client_library_specifier> | <library_bits> }  
[, PLATFORM = WINDOWS ])  
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

Библиотеки добавляются в базу данных с областью, ограниченной пользователем. Имена библиотек должны быть уникальными в контексте определенного пользователя или владельца. Например, два пользователя **RUser1** и **RUser2** могут загрузить библиотеку R `ggplot2` индивидуально и по отдельности. Но если пользователь **RUser1** хочет отправить новую версию `ggplot2`, второму экземпляру нужно присвоить другое имя либо он должен заменить существующую библиотеку. 

Имена библиотек не могут присваиваться произвольным образом. Имя библиотеки должно быть таким же, как имя, необходимое для загрузки библиотеки R из R.

**owner_name**

Указывает имя пользователя или роли, которой принадлежит внешняя библиотека. Если атрибут не указан, владельцем становится текущий пользователь.

Библиотеки, принадлежащие владельцу базы данных, считаются глобальными по отношению к базе данных и среде выполнения. Иными словами, владельцы базы данных могут создавать библиотеки, которые содержат общий набор библиотек или пакетов, совместно используемых несколькими пользователями. Если внешнюю библиотеку создает другой пользователь, кроме пользователя `dbo`, к этой внешней библиотеке будет иметь доступ только этот пользователь.

Когда пользователь **RUser1** выполняет сценарий R, значение `libPath` может содержать несколько путей. Первый путь всегда является путем к общей библиотеке, созданной владельцем базы данных. Во второй части `libPath` указывается путь, содержащий пакеты, загруженные отдельно пользователем **RUser1**.

**file_spec**

Указывает содержимое пакета для конкретной платформы. Поддерживается только один файл артефакта на платформу.

Файл можно указать в виде локального или сетевого пути.

При необходимости можно указать платформу операционной системы для файла. Для каждой платформы операционной системы для конкретного языка или среды выполнения разрешен только один артефакт файла или содержимое.

**library_bits**

Задает содержимое пакета как шестнадцатеричный литерал, аналогично сборкам. 

Этот параметр полезен, если необходимо создать библиотеку или изменить существующую библиотеку (и у вас есть необходимые разрешения), но файловая система на сервере ограничена, и не удается скопировать файлы библиотеки в место, доступное для сервера.

**PLATFORM = WINDOWS**

Указывает платформу для содержимого библиотеки. Является значением по умолчанию для платформы узла, на которой выполняется SQL Server. Поэтому пользователю не нужно указывать это значение. Оно необходимо в случае, когда поддерживается несколько платформ или пользователь хочет указать другую платформу. 

В SQL Server 2017 поддерживается только платформа Windows.

## <a name="remarks"></a>Remarks

При использовании файла в языке R пакеты должны быть подготовлены в виде сжатых архивных файлов с расширением ZIP для Windows. В настоящее время поддерживается только платформа Windows. 

Инструкция `CREATE EXTERNAL LIBRARY` загружает биты библиотеки в базу данных. Библиотека устанавливается, когда пользователь запускает внешний скрипт с помощью [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) и вызывает пакет или библиотеку.

Библиотеки, загруженные в экземпляр, могут быть открытыми или закрытыми. Если библиотека создается членом `dbo`, она является открытой и может использоваться всеми пользователями. В противном случае библиотека является закрытой и доступна только этому пользователю.

## <a name="permissions"></a>Разрешения

Требуется разрешение `CREATE EXTERNAL LIBRARY`. По умолчанию любой пользователь с учетной записью **dbo**, являющийся членом роли **db_owner**, имеет разрешения на создание внешней библиотеки. Другим пользователям необходимо явным образом предоставить разрешение с помощью инструкции [GRANT](https://docs.microsoft.com/sql/t-sql/statements/grant-database-permissions-transact-sql), указав CREATE EXTERNAL LIBRARY в качестве привилегии.

Для изменения библиотеки требуется отдельное разрешение `ALTER ANY EXTERNAL LIBRARY`.

## <a name="examples"></a>Примеры

### <a name="a-add-an-external-library-to-a-database"></a>A. Добавление внешней библиотеки в базу данных  

В следующем примере внешняя библиотека `customPackage` добавляется в базу данных.

```sql
CREATE EXTERNAL LIBRARY customPackage
FROM (CONTENT = 'C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\customPackage.zip') WITH (LANGUAGE = 'R');
```

После успешной загрузки библиотеки в экземпляр пользователь выполняет процедуру `sp_execute_external_script`, чтобы установить библиотеку.

```sql
EXEC sp_execute_external_script 
@language =N'R', 
@script=N'library(customPackage)'
```

### <a name="b-installing-packages-with-dependencies"></a>Б. Установка пакетов с зависимостями

Если вы хотите установить пакет с зависимостями, нужно обязательно проанализировать зависимости первого и второго уровней и убедиться, что все необходимые пакеты доступны, _до_ установки целевого пакета.

Предположим, вы хотите установить новый пакет `packageA`:

+ `packageA` имеет зависимость от `packageB`
+ `packageB` имеет зависимость от `packageC`

Для успешной установки `packageA` необходимо создать библиотеки для `packageB` и `packageC` одновременно с добавлением `packageA` в SQL Server. Не забудьте проверить версии необходимых пакетов.

На практике зависимости популярных пакетов обычно гораздо сложнее, чем в этом простом примере. Например, **ggplot2** может требовать более 30 пакетов, а эти пакеты могут требовать дополнительные пакеты, которые недоступны на сервере. Отсутствие пакета или наличие пакета неправильной версии могут привести к сбою установки.

Так как может быть трудно определить все зависимости при просмотре манифеста пакета, рекомендуем использовать такой пакет, как [miniCRAN](https://cran.r-project.org/web/packages/miniCRAN/index.html), для поиска всех пакетов, необходимых для успешного завершения установки.

+ Загрузите целевой пакет и его зависимости. Все файлы должны находиться в папке, доступной на сервере.

    ```sql
    CREATE EXTERNAL LIBRARY packageA 
    FROM (CONTENT = 'C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\packageA.zip') 
    WITH (LANGUAGE = 'R'); 
    GO

    CREATE EXTERNAL LIBRARY packageB FROM (CONTENT = 'C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\packageB.zip') 
    WITH (LANGUAGE = 'R');
    GO

    CREATE EXTERNAL LIBRARY packageC FROM (CONTENT = 'C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\packageC.zip') 
    WITH (LANGUAGE = 'R');
    GO
    ```

+ Сначала установите необходимые пакеты.

    Если необходимый пакет уже отправлен экземпляру, не нужно добавлять его снова. Просто не забудьте проверить версию существующего пакета. 
    
    Необходимые пакеты `packageC` и `packageB` установлены в правильном порядке, когда `sp_execute_external_script` впервые запускается для установки пакета `packageA`.

    Но если доступны не все необходимые пакеты, установка целевого пакета `packageA` завершается ошибкой.

    ```sql
    EXEC sp_execute_external_script 
    @language =N'R', 
    @script=N'
    # load the desired package packageA
    library(packageA)
    print(packageVersion("packageA"))
    '
    ```

### <a name="c-create-a-library-from-a-byte-stream"></a>В. Создание библиотеки из потока байтов

Если у вас нет возможности сохранить файлы пакета на сервере, вы можете передать содержимое пакетов в переменной. В следующем примере библиотека создается путем передачи битов в виде шестнадцатеричного литерала.

```SQL
CREATE EXTERNAL LIBRARY customLibrary FROM (CONTENT = 0xabc123) WITH (LANGUAGE = 'R');
```

> [!NOTE]
> В этом примере кода показан только синтаксис. Двоичное значение в `CONTENT =` было усечено для удобства чтения и не создает рабочую библиотеку. Фактическое содержимое двоичной переменной будет гораздо длиннее.

### <a name="d-change-an-existing-package-library"></a>Г. Изменение существующей библиотеки пакета

Можно использовать инструкцию DDL `ALTER EXTERNAL LIBRARY` для добавления нового содержимого библиотеки или изменения существующего содержимого библиотеки. Для изменения существующей библиотеки требуется разрешение `ALTER ANY EXTERNAL LIBRARY`.

Дополнительные сведения см. в разделе [ALTER EXTERNAL LIBRARY](alter-external-library-transact-sql.md).

## <a name="see-also"></a>См. также раздел

[ALTER EXTERNAL LIBRARY (Transact-SQL)](alter-external-library-transact-sql.md)  
[DROP EXTERNAL LIBRARY (Transact-SQL)](drop-external-library-transact-sql.md)  
[sys.external_library_files](../../relational-databases/system-catalog-views/sys-external-library-files-transact-sql.md)  
[sys.external_libraries](../../relational-databases/system-catalog-views/sys-external-libraries-transact-sql.md)  
