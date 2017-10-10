---
title: "Создание ВНЕШНЕЙ БИБЛИОТЕКИ (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 10/05/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
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
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 29122bdf543e82c1f429cf401b5fe1d8383515fc
ms.openlocfilehash: 8066d267790f346a22a649fb0c873a3d454489a8
ms.contentlocale: ru-ru
ms.lasthandoff: 10/10/2017

---
# <a name="create-external-library-transact-sql"></a>Создание ВНЕШНЕЙ БИБЛИОТЕКИ (Transact-SQL)  

[!INCLUDE[tsql-appliesto-ssvnxt-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssvnxt-xxxx-xxxx-xxx.md)]  

Отправляет пакеты R в базу данных из указанного байтового потока или путь к файлу.

Эта инструкция служит универсальный механизм администратор базы данных могут отправлять артефакты, необходимые для любой новой внешней среды (R, Python, Java, т. д.) и платформы операционной системы, поддерживаемые [!INCLUDE[ssnoversion](../../includes/ssnoversion.md)]. В настоящее время поддерживаются только язык R и на платформе Windows.

## <a name="syntax"></a>Синтаксис

```
CREATE EXTERNAL LIBRARY library_name  
    [ AUTHORIZATION owner_name ]  
FROM <file_spec> [,…2]  
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

Библиотеки добавляются в базу данных, областью действия пользователя. То есть имена библиотек, считаются уникальными в контексте определенного пользователя или владелец и библиотеки имена должны быть уникальными для каждого пользователя. Например, два пользователя **RUser1** и **RUser2** как отдельно, так и по отдельности загружаемых библиотеки R `ggplot2`.

**owner_name**

Указывает имя пользователя или роли, которой принадлежит внешней библиотеки. Если атрибут не указан, владельцем становится текущий пользователь.

Библиотеки, принадлежащий владельцу базы данных, считаются глобальными по отношению к базе данных и среды выполнения. Иными словами владельцы базы данных можно создавать библиотеки, которые содержат общий набор библиотек или пакеты, которые совместно используется несколькими пользователями. Внешней библиотеки создания пользователем, отличный от `dbo` пользователя, внешние библиотеки является закрытым только этому пользователю.

Когда пользователь **RUser1** выполняет сценарий R, а значение `libPath` может содержать несколько путей. Первый путь всегда является путь к общей библиотеки, созданных владельцем базы данных. Во второй части `libPath` указывает путь, содержащий пакеты загружен отдельно с **RUser1**.

**file_spec**

Указывает содержимое пакета для конкретной платформы. Поддерживается только один файл артефакта каждой платформы.

Файл можно указать в виде локальный путь или сетевой путь.

При необходимости можно указать платформу операционной системы для файла. Для каждой платформы операционной системы для конкретного языка или среды выполнения разрешена артефакта только один файл или содержимое.

**library_bits**

Задает содержимое пакета как Шестнадцатеричный литерал, аналогично сборки. Этот параметр позволяет пользователям создавать библиотеки для изменения библиотеки, если они имеют необходимое разрешение, но не имеют доступ к пути файла в папку, для которой у сервера есть доступ.

**ПЛАТФОРМА = WINDOWS**

Указывает платформу для библиотеки содержимого. Значение по умолчанию платформа узла, на котором выполняется SQL Server. Таким образом что пользователь не имеет для указания значения. Он необходим в случае которых поддерживаются несколько платформ, или пользователь должен указать другой платформе. Windows является единственным поддерживаемой платформы.

## <a name="remarks"></a>Замечания

Пакеты для языка R, при использовании файла, необходимо подготовить в виде ZIP-архив файлов с. ПОЧТОВЫЙ модуль для Windows. В настоящее время поддерживается только на платформу Windows

`CREATE EXTERNAL LIBRARY` Инструкции только отправляет биты библиотеки в базе данных. Библиотеки, фактически не устанавливается, пока пользователь запускает внешнего скрипта после него, выполнив [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).  

Библиотеки переданы экземпляр может быть открытой или закрытой. Если библиотека создается с членом `dbo`, библиотека является открытым и может использоваться совместно с всех пользователей. В противном случае библиотеки является частным только этому пользователю.

Большие двоичные объекты нельзя использовать в качестве источника данных в выпуске 2017 г. SQL Server.

## <a name="permissions"></a>Permissions

Требуется `CREATE ANY EXTERNAL LIBRARY` разрешение.

Для изменения библиотеки требует отдельного разрешения `ALTER ANY EXTERNAL LIBRARY`.

## <a name="examples"></a>Примеры

### <a name="a-add-an-external-library-to-a-database"></a>A. Добавление внешней библиотеки в базу данных  

В следующем примере добавляется внешней библиотеки вызывается customPackage в базе данных.

```sql
CREATE EXTERNAL LIBRARY customPackage 
FROM 
  (CONTENT = 'C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\customPackage.zip')
WITH (LANGUAGE = 'R');
```  

После библиотеке успешно отправлен на экземпляр, пользователь выполняет `sp_execute_external_script` процедуру, чтобы установить библиотеку.

```sql
EXEC sp_execute_external_script 
@language =N'R', 
@script=N'
# load customPackage
library(customPackage)
'
```

### <a name="b-installing-packages-with-dependencies"></a>Б. Установка пакетов с зависимостями

Если `packageB` имеет зависимость от `packageA`, затем выполните эти общие принципы:

+ Загрузите целевой пакет и его зависимости.

    Оба пакета должны находиться в папке, доступный на сервере.

    ```sql
    CREATE EXTERNAL LIBRARY packageA 
    FROM (CONTENT = 'C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\packageA.zip') 
    WITH (LANGUAGE = 'R'); 
    
    CREATE EXTERNAL LIBRARY packageB FROM (CONTENT = 'C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\packageB.zip') 
    WITH (LANGUAGE = 'R');
    ```

+ Сначала установлены зависимости.

    Если требуемый пакет `packageA` уже был отправлен на экземпляр, его нужно не был установлен отдельно. Требуемый пакет `packageA` будет установлен при `sp_execute_external_script` при первом запуске для установки пакета `packageB`.

    Тем не менее если требуемый пакет `packageA`, недоступен, установка пакета целевой `packageB` завершится ошибкой.

    ```sql
    EXEC sp_execute_external_script 
    @language =N'R', 
    @script=N'
    # load packageB
    library(packageB)
    # call customPackageBFunc
    OutputDataSet <- customPackageBFunc()
    '
    with result sets (([result] int));    
    ```

### <a name="c-create-a-library-from-a-byte-stream"></a>В. Создание библиотеки из потока байтов

В следующем примере создается библиотеку, передавая обновленные bits в шестнадцатеричном представлении литерала.

```SQL
CREATE EXTERNAL LIBRARY customLibrary FROM (CONTENT = 0xabc123) WITH (LANGUAGE = 'R');
```

### <a name="d-change-an-existing-package-library"></a>Г. Изменение существующего пакета библиотеки

`ALTER EXTERNAL LIBRARY` Инструкции DDL можно использовать для добавления нового содержимого библиотеки или изменения существующего содержимого библиотеки. Для изменения существующей библиотеки требуется `ALTER ANY EXTERNAL LIBRARY` разрешение.

Дополнительные сведения см. в разделе [ALTER ВНЕШНЕЙ БИБЛИОТЕКИ](alter-external-library-transact-sql.md).

### <a name="e-delete-a-package-library"></a>Д. Удаление библиотеки пакета

Чтобы удалить библиотеку пакет из базы данных, выполните инструкцию.

```sql
DROP EXTERNAL LIBRARY customPackage <user_name>;
```

> [!NOTE]
> В отличие от других `DROP` инструкций в [!INCLUDE[ssnoversion](../../includes/ssnoversion.md)], эта инструкция поддерживает дополнительный параметр, который задает центр пользователя. Этот параметр позволяет пользователям с ролями владения по удалению библиотек, загруженных с обычных пользователей.

## <a name="see-also"></a>См. также:

[ALTER ВНЕШНЕЙ БИБЛИОТЕКИ (Transact-SQL)](alter-external-library-transact-sql.md)  
[DROP ВНЕШНЕЙ БИБЛИОТЕКИ (Transact-SQL)](drop-external-library-transact-sql.md)  
[sys.external_library_files](../../relational-databases/system-catalog-views/sys-external-library-files-transact-sql.md)  
[sys.external_libraries](../../relational-databases/system-catalog-views/sys-external-libraries-transact-sql.md)  

