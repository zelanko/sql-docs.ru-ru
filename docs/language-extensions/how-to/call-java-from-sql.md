---
title: Вызов среды выполнения Java
titleSuffix: SQL Server Language Extensions
description: Узнайте, как вызывать классы Java из хранимых процедур SQL Server с помощью расширений языка SQL Server.
author: dphansen
ms.author: davidph
ms.date: 06/25/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: language-extensions
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 5aa8659b57349efb7378209006bbada148206bcb
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85735121"
---
# <a name="how-to-call-the-java-runtime-in-sql-server-language-extensions"></a>Вызов среды выполнения Java в расширениях языка SQL Server
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

[Расширения языка SQL Server](../language-extensions-overview.md) используют системную хранимую процедуру [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) в качестве интерфейса для вызова среды выполнения Java. 

В этой статье описываются детали реализации классов и методов Java, которые выполняются в SQL Server.

## <a name="where-to-place-java-classes"></a>Место размещения классов Java

Существует два метода вызова классов Java в SQL Server:

1. Поместить файлы **. class** или **. jar** в [подкаталог классов Java (classpath)](#classpath). 

2. Загрузить скомпилированные в файл **. jar** классы и другие зависимости в базу данных с помощью инструкции DDL для [внешней библиотеки](#external-library). 

> [!NOTE]
> В качестве общей рекомендации следует использовать файлы **. jar**, а не отдельные файлы **. class**. Это распространенная методика при работе с языком Java, которая в целом упрощает работу. См. также статью о том, [как создать JAR-файл из файлов классов](create-a-java-jar-file-from-class-files.md).

<a name="classpath"></a>

## <a name="use-classpath"></a>Использование подкаталогов классов (classpath)

### <a name="basic-principles"></a>Основные принципы

Ниже приведены некоторые основные принципы при выполнении Java на SQL Server.

* Скомпилированные пользовательские классы Java должны находиться в файлах **. class** или **. jar** в подкаталогах классов Java. [Параметр CLASSPATH](#set-classpath) определяет путь к скомпилированным файлам Java. 

* Метод Java, который вы вызываете, должен быть указан в параметре **script** в хранимой процедуре.

* Если класс принадлежит к пакету, необходимо задать параметр **packageName**.

* Параметр **params** используется для передачи параметров в класс Java. Вызов метода, для которого требуются аргументы, не поддерживается. Поэтому параметры являются единственным способом передавать значения аргументов в метод. 

> [!NOTE]
> В этом примечании приведены сведения о поддерживаемых и неподдерживаемых операциях в SQL Server 2019 версии-кандидате 1, относящиеся к Java.
> * В хранимой процедуре поддерживаются входные параметры. Выходные параметры не поддерживаются.

### <a name="call-java-class"></a>Вызов класса Java

Системная хранимая процедура [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) является интерфейсом для вызова среды выполнения Java. В следующем примере показан вызов `sp_execute_external_script` с использованием расширения Java и параметров для указания пути, сценария и пользовательского кода.

> [!NOTE]
> Обратите внимание, что не нужно указывать, какой вызывать метод. По умолчанию вызывается метод с именем **execute**. Это означает, что необходимо следовать требованиям [пакета расширяемости SDK для Java в SQL Server](extensibility-sdk-java-sql-server.md) и реализовать метод execute в классе Java.

```sql
DECLARE @param1 int
SET @param1 = 3

EXEC sp_execute_external_script
  @language = N'Java'
, @script = N'<packageName>.<ClassName>'
, @input_data_1 = N'<Input Query>'
, @param1 = @param1
```

<a name="set-classpath"></a>

### <a name="set-classpath"></a>Определение подкаталогов классов (CLASSPATH)

После компиляции класса или классов Java и создания JAR-файла в подкаталоге классов Java существует два способа передачи подкаталогов классов (classpath) в расширение языка Java в SQL Server:

1. Использовать внешние библиотеки

    Самый простой способ — сделать так, чтобы SQL Server автоматически находил классы, создав внешние библиотеки и указав в библиотеке расположение JAR-файла. [Использование внешних библиотек для Java](#external-library)

2. Зарегистрировать системную переменную среды

    Можно создать системную переменную среды и указать пути к JAR-файлу, содержащему классы. Создайте системную переменную среды с именем **CLASSPATH**.

<a name="external-library"></a>

## <a name="use-external-library"></a>Использование внешней библиотеки

В SQL Server 2019 версии-кандидате 1 можно использовать внешние библиотеки для языка Java в Windows и Linux. Можно скомпилировать классы в JAR-файл и передать этот файл и другие зависимости в базу данных с помощью инструкции DDL [CREATE EXTERNAL LIBRARY](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql).

Пример передачи JAR-файла с помощью внешней библиотеки:

```sql 
CREATE EXTERNAL LIBRARY myJar
FROM (CONTENT = '<local path to .jar file>') 
WITH (LANGUAGE = 'Java'); 
GO
```

Создав внешнюю библиотеку, SQL Server автоматически получает доступ к классам Java, и вам не нужно задавать специальные разрешения для подкаталогов классов.

Пример вызова метода в классе из пакета, переданного в виде внешней библиотеки:

```sql
EXEC sp_execute_external_script
  @language = N'Java'
, @script = N'MyPackage.MyCLass'
, @input_data_1 = N'SELECT * FROM MYTABLE'
with result sets ((column1 int))
```

Дополнительные сведения см. в разделе [CREATE EXTERNAL LANGUAGE](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql).

## <a name="loopback-connection-to-sql-server"></a>Подключение к SQL Server с замыканием на себя

Используйте подключение с замыканием на себя для обратного соединения с SQL Server через JDBC с целью чтения или записи данных из кода Java, выполняемого с помощью процедуры `sp_execute_external_script`. Его можно применять, если нельзя использовать аргументы **InputDataSet** и **OutputDataSet** процедуры `sp_execute_external_script`.
Чтобы установить подключение с замыканием на себя в Windows, используйте следующий пример.

```
jdbc:sqlserver://localhost:1433;databaseName=Adventureworks;integratedSecurity=true;
``` 

Для установки подключения с замыканием на себя в Linux драйверу JDBC требуются три свойства подключения, определенные в следующем сертификате.

[Client-Certificate-Authenication](https://github.com/microsoft/mssql-jdbc/wiki/Client-Certificate-Authentication-for-Loopback-Scenarios)


## <a name="next-steps"></a>Дальнейшие действия

+ [Руководство. Поиск строки с использованием регулярных выражений в Java](../tutorials/search-for-string-using-regular-expressions-in-java.md)
