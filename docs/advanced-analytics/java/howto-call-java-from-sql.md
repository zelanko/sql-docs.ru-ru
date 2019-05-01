---
title: Как вызвать Java из SQL - службы машинного обучения SQL Server
description: Узнайте, как вызывать классы Java из хранимых процедур SQL Server с помощью программирования расширение языка в SQL Server 2019 Java.
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/23/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: a75878ccc4f14d03f84102dd48bfd43a6e04daea
ms.sourcegitcommit: bd5f23f2f6b9074c317c88fc51567412f08142bb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2019
ms.locfileid: "63473558"
---
# <a name="how-to-call-java-from-sql-server-2019-preview"></a>Как вызвать Java из предварительной версии SQL Server 2019

При использовании [расширение языка Java](extension-java.md), [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) система, хранимая процедура — это интерфейс, используемый для вызова среды выполнения Java. Разрешения в базе данных, применяются к выполнению кода Java.

В этой статье объясняется, сведения о реализации для Java классы и методы, которые выполняются на сервере SQL Server. Если вы знакомы со следующими сведениями, просмотрите [пример Java](java-first-sample.md) следующим шагом.

Существует два метода для вызова классами Java в SQL Server:

1. Поместите .class или .jar файлов в вашей [Java classpath](#classpath). Эта возможность доступна для Windows и Linux.

2. Отправка скомпилированных классов в JAR-файл и другие зависимости в базу данных при помощи [внешняя библиотека](#external-library) DDL. Этот параметр доступен для Windows и Linux из CTP 2.4.

> [!NOTE]
> Как общие рекомендации используйте JAR-файлы и файлы не отдельных .class. Это распространенная практика в Java и облегчит общее удобство работы. См. также [Создание JAR-файл из файлов класса](extension-java.md#create-jar).

<a name="classpath"></a>

## <a name="classpath"></a>Путь к классу

### <a name="basic-principles"></a>Основные принципы

* Скомпилированный пользовательские классы Java должен существовать в файлы .class или JAR-файлы в классам Java. [Параметр CLASSPATH](#set-classpath) путь скомпилированные файлы Java. 

* При вызове метода Java необходимо указать в параметре «скрипт» для хранимой процедуры.

* Если этот класс принадлежит к пакету, «имя пакета» должен предоставить.

* «params» используется для передачи параметров в класс Java. Вызов метода, который требует аргументов не поддерживается, что делает параметры единственным способом передать значения аргумента в метод. 

> [!Note]
> Эта заметка формулирующее поддерживаемые и неподдерживаемые операций, относящихся к Java в CTP-версии 2.x.
> * Для хранимой процедуры поддерживаются входных параметров. Выходные параметры не являются.
> * Потоковая передача с помощью параметра sp_execute_external_script @r_rowsPerRead не поддерживается.
> * Секционирование с помощью @input_data_1_partition_by_columns не поддерживается.
> * При параллельной обработке с помощью @parallel= 1 поддерживается.

### <a name="call-java-class"></a>Вызовите класс Java

Применимо к Windows и Linux, [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) система, хранимая процедура — это интерфейс, используемый для вызова среды выполнения Java. В следующем примере показано sp_execute_external_script, используя расширение Java и параметры для указания пути, скрипты и пользовательский код.

> [!NOTE]
> Обратите внимание, что вам не нужно определять вызываемый метод. По умолчанию вызывается метод **выполнение** вызывается. Это означает необходимость выполните пакет SDK и реализовывать метод execute в классе Java.

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

### <a name="set-classpath"></a>Задать путь к КЛАССУ

После компиляции класс Java или классов и JAR-файл создан в ваш путь к классу Java, у вас есть два варианта предоставления пути к классам в расширение SQL Server Java:

**Вариант 1. Использовать внешние библиотеки** самый простой вариант — сделать сервер SQL Server автоматически находить ваши классы, создание внешние библиотеки и библиотеки JAR-файл. [Использовать внешние библиотеки для Java](howto-call-java-from-sql.md#external-library)

**Вариант 2. Регистрация системной переменной среды**

Так же, как вы создали переменной среды операционной системы для среды выполнения Java, можно создать переменную среды и указываются пути к файлу JAR-файл, содержащий классы. Чтобы сделать это, необходимо создать системную переменную среды с именем «Путь к КЛАССУ».

<a name="external-library"></a>

## <a name="external-library"></a>Внешняя библиотека

В SQL Server 2019 CTP 2.4 внешние библиотеки можно использовать для языка Java в Windows и Linux. Можно скомпилировать свои классы в JAR-файл и отправить JAR-файл и другие зависимости в базу данных при помощи [CREATE EXTERNAL LIBRARY](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql) DDL.

Пример того, как отправить JAR-файл с помощью внешней библиотеки.

```sql 
CREATE EXTERNAL LIBRARY myJar
FROM (CONTENT = '<local path to .jar file>') 
WITH (LANGUAGE = 'Java'); 
GO
```

Создание внешней библиотеки, SQL Server автоматически будет иметь доступ к классам Java и вы не обязательно для задания специальных разрешений для пути к классам.

Пример вызова метода в классе из пакета отправить в виде внешней библиотеки:

```sql
EXEC sp_execute_external_script
  @language = N'Java'
, @script = N'MyPackage.MyCLass'
, @input_data_1 = N'SELECT * FROM MYTABLE'
with result sets ((column1 int))
```

Дополнительные сведения см. в разделе [CREATE EXTERNAL LIBRARY](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql).

## <a name="next-steps"></a>Следующие шаги

+ [Пример Java в SQL Server](java-first-sample.md)
+ [Типы данных Java и SQL Server](java-sql-datatypes.md)
+ [Расширение языка Java в SQL Server](extension-java.md)
