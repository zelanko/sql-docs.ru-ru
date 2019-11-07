---
title: CREATE EXTERNAL LANGUAGE (Transact-SQL) — SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2019
ms.prod: sql
ms.reviewer: dphansen
ms.technology: language-extensions
ms.topic: language-reference
author: nelgson
ms.author: negust
manager: cgronlun
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 3f2911406b902ea4d4e7840676dcf08b0318664d
ms.sourcegitcommit: 830149bdd6419b2299aec3f60d59e80ce4f3eb80
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/04/2019
ms.locfileid: "73536242"
---
# <a name="create-external-language-transact-sql"></a>CREATE EXTERNAL LANGUAGE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Регистрирует расширения внешнего языка в базе данных из заданного пути файла или байтового потока. Эта инструкция служит универсальным механизмом для администратора базы данных, позволяющим регистрировать новые расширения внешнего языка на любой платформе операционной системы, поддерживаемой SQL Server. См подробнее о [расширениях языка](https://docs.microsoft.com/sql/language-extensions/language-extensions-overview).

> [!NOTE]
> Сейчас только **Java** поддерживается как внешний язык. **R** и **Python** являются зарезервированными именами, поэтому создать внешние языки с такими именами невозможно. См. подробнее об использовании **R** и **Python** в документации по [Службам машинного обучения SQL Server](https://docs.microsoft.com/sql/advanced-analytics/).

## <a name="syntax"></a>Синтаксис

```text
CREATE EXTERNAL LANGUAGE language_name  
[ AUTHORIZATION owner_name ]  
FROM <file_spec> [ ,...2 ]  
WITH (<option_spec>)
[ ; ]  

<file_spec> ::=  
{
    ( CONTENT = { <external_lang_specifier> | <content_bits>,
    FILE_NAME = <external_lang_file_name>
    [ , PLATFORM = <platform> ]
    [ , PARAMETERS = <external_lang_parameters> ]
    [ , ENVIRONMENT_VARIABLES = <external_lang_env_variables> )
}

<external_lang_specifier> :: =  
{
    '[file_path\]os_file_name'  
}

<content_bits> :: =  
{
    varbinary_literal
    | varbinary_expression
}

<external_lang_file_name> :: =  
'extension_file_name'


<platform> :: =
{
    WINDOWS
  | LINUX
}

<external_lang_parameters> :: =  
'extension_specific_parameters'
```

### <a name="arguments"></a>Аргументы

**language_name**

Языки являются объектами в области базы данных. Имена языков должны быть уникальными в пределах базы данных.

**owner_name**

Указывает имя пользователя или роли, которым принадлежит внешний язык. Если атрибут не указан, владельцем становится текущий пользователь. В зависимости от разрешений может потребоваться предоставить другим пользователям явное разрешение на выполнение скриптов с использованием соответствующего языка.

**file_spec**

Указывает содержимое расширения языка. Для конкретного языка на отдельной платформе разрешено использовать только одну спецификацию файла.

**external_lang_specifier**

Полный путь к файлу ZIP или TAR.GZ, содержащему код расширений. Это содержимое может быть путем к файлу ZIP (в Windows) или TAR.GZ (в Linux).

**content_bits**

Указывает содержимое языка в виде шестнадцатеричного литерала, аналогично сборкам.

Этот параметр полезен, если нужно создать язык или изменить существующий язык (и у вас есть необходимые разрешения), но файловая система на сервере ограничена, и не удается скопировать файлы библиотеки в место, доступное для сервера.

**external_lang_file_name**

Имя файла расширения DLL или SO. Этот параметр нужен для идентификации правильного файла в случаях, когда в файле ZIP и TAR.GZ <external_lang_specifier> существует несколько файлов DLL или SO.

**external_lang_parameters**

Этот параметр позволяет предоставить среде выполнения внешнего языка набор параметров. Значения параметров предоставляются внешней среде выполнения после запуска внешнего процесса. Однако переменные среды становятся доступны расширению языка до запуска внешнего процесса.

**external_lang_env_variables**

Этот параметр позволяет предоставить среде выполнения внешнего языка набор переменных среды до запуска внешнего процесса. Примером переменной среды является домашний каталог самой среды выполнения. Пример: JRE_HOME.

**platform**

Этот параметр необходим для гибридных сценариев операционной системы. В гибридной архитектуре язык требуется регистрировать один раз для каждой платформы. Имя языка и платформы будет уникальным ключом для каждого внешнего языка. Если платформа не указана, предполагается текущая операционная система.

## <a name="remarks"></a>Remarks

В настоящее время **PARAMETERS** и **ENVIRONMENT_VARIABLES** не поддерживаются.

## <a name="permissions"></a>Разрешения

Требуется разрешение `CREATE EXTERNAL LANGUAGE`. По умолчанию любой пользователь с учетной записью **dbo**, являющийся членом роли **db_owner**, имеет разрешения на создание внешнего языка. Другим пользователям необходимо явным образом предоставить разрешение с помощью инструкции [GRANT](https://docs.microsoft.com/sql/t-sql/statements/grant-database-permissions-transact-sql), указав CREATE EXTERNAL LANGUAGE в качестве привилегии.

Для изменения библиотеки требуется отдельное разрешение `ALTER ANY EXTERNAL LANGUAGE`.

### <a name="execute-external-script-permission"></a>Разрешение EXECUTE EXTERNAL SCRIPT

Вы можете использовать разрешения EXECUTE EXTERNAL SCRIPT, чтобы можно было предоставлять разрешения на выполнение внешних скриптов для определенных языков. Это отличается от разрешения EXECUTE ANY EXTERNAL SCRIPT, которое не позволяло предоставлять разрешение на выполнение для определенного языка.

Это означает, что пользователям без учетной записи **dbo** нужно предоставить разрешения на выполнение конкретного языка:

```sql
GRANT EXECUTE EXTERNAL SCRIPT ON EXTERNAL LANGUAGE ::language_name 
TO database_principal_name;
```

### <a name="reference-permissions-to-external-libraries"></a>Ссылочные разрешения на внешние библиотеки

По аналогии со сборками для внешних языков нужны ссылочные разрешения, чтобы образовать связь между внешними библиотеками и внешними языками. Например, если планируется удалить внешний язык, сначала пользователь должен убедиться, что удалены все внешние библиотеки, ссылающиеся на этот язык. Вы можете просмотреть внешний язык в иерархии как объект более высокого уровня, чем внешние библиотеки.

## <a name="examples"></a>Примеры

### <a name="a-create-an-external-language-in-a-database"></a>A. Создание внешнего языка в базе данных  

Следующий пример добавляет внешний язык Java в базу данных на сервере SQL Server в Windows.

```sql
CREATE EXTERNAL LANGUAGE Java 
FROM (CONTENT = N'<path-to-zip>', FILE_NAME = 'javaextension.dll');
GO
```

### <a name="b-create-an-external-language-for-both-windows-and-linux"></a>Б. Создание внешнего языка одновременно для Windows и Linux

Вы можете указать два параметра `<file_spec>`: один для Windows, а другой для Linux.

```sql
CREATE EXTERNAL LANGUAGE Java
FROM
(CONTENT = N'<path-to-zip>', FILE_NAME = 'javaextension.dll', PLATFORM = WINDOWS),
(CONTENT = N'<path-to-tar.gz>', FILE_NAME = 'javaextension.so', PLATFORM = LINUX);
GO
```
### <a name="c-grant-permissions-to-execute-external-script"></a>В. Предоставление разрешений на выполнение внешнего скрипта

В приведенном ниже примере субъекту **mylogin** предоставляется доступ для выполнения скрипта с использованием внешнего языка **Java**.

```sql
GRANT EXECUTE EXTERNAL SCRIPT ON EXTERNAL LANGUAGE ::Java 
TO mylogin;
```


## <a name="see-also"></a>См. также раздел

[ALTER EXTERNAL LANGUAGE (Transact-SQL)](alter-external-language-transact-sql.md)  
[DROP EXTERNAL LANGUAGE (Transact-SQL)](drop-external-language-transact-sql.md)  
[sys.external_languages](../../relational-databases/system-catalog-views/sys-external-languages-transact-sql.md)  
[sys.external_language_files](../../relational-databases/system-catalog-views/sys-external-language-files-transact-sql.md)  
