---
title: Как вызвать Java из SQL - службы машинного обучения SQL Server
description: Узнайте, как вызывать классы Java из хранимых процедур SQL Server с помощью программирования расширение языка в SQL Server 2019 Java.
ms.prod: sql
ms.technology: machine-learning
ms.date: 03/27/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 36a949f4d046d4071ffd7d52d34233e993ee700f
ms.sourcegitcommit: 2db83830514d23691b914466a314dfeb49094b3c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58493006"
---
# <a name="how-to-call-java-from-sql-server-2019-preview"></a>Как вызвать Java из предварительной версии SQL Server 2019

При использовании [расширение языка Java](extension-java.md), [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) система, хранимая процедура — это интерфейс, используемый для вызова среды выполнения Java. Разрешения в базе данных, применяются к выполнению кода Java.

В этой статье объясняется, сведения о реализации для Java классы и методы, которые выполняются на сервере SQL Server. Если вы знакомы со следующими сведениями, просмотрите [пример Java](java-first-sample.md) следующим шагом.

Существует два метода для вызова классами Java в SQL Server:

1. Поместите .class или .jar файлов в вашей [Java classpath](#classpath). Эта возможность доступна для Windows и Linux.

2. Отправка скомпилированных классов в JAR-файл и другие зависимости в базу данных при помощи [внешняя библиотека](#external-library) DDL. Этот параметр доступен для Windows и Linux в CTP 2.4.

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

### <a name="call-class"></a>Класс Call

Применимо к Windows и Linux, [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) система, хранимая процедура — это интерфейс, используемый для вызова среды выполнения Java. В следующем примере показано sp_execute_external_script, используя расширение Java и параметры для указания пути, скрипты и пользовательский код.

```sql
DECLARE @myClassPath nvarchar(30)
DECLARE @param1 int

SET @myClassPath = N'/<my path>/program.jar'
SET @param1 = 3

EXEC sp_execute_external_script
  @language = N'Java'
, @script = N'<packageName>.<ClassName>.<methodName>'
, @input_data_1 = N'<Input Query>'
, @params = N'@CLASSPATH nvarchar(30), @param1 INT'
, @CLASSPATH = @myClassPath
, @param1 = @param1
```

<a name="set-classpath"></a>

### <a name="set-classpath"></a>Задать путь к КЛАССУ

После компиляции класс Java или классов и поместить файлы .class или JAR-файлы в ваш путь к классу Java, у вас есть два варианта предоставления пути к классам в расширение SQL Server Java:

**Вариант 1. Передать в качестве параметра**

Одним из подходов для указания пути к скомпилированным кодом является, задав пути к КЛАССАМ в качестве входного параметра для процедуры sp_execute_external_script. [Пример Java](java-first-sample.md#call-method) этот метод продемонстрирован. Если вы выбрали этот подход и использовать несколько путей, обязательно используйте разделитель пути, который является допустимым для операционной системы:

* В Linux, разделяйте путей в пути к КЛАССАМ с запятой «:».
* В Windows, пути в пути к КЛАССУ следует разделять точкой с запятой «;»

**Вариант 2. Регистрация системной переменной**

Так же, как вы создали системную переменную для JDK исполняемых файлов, можно создать системную переменную для пути кода. Чтобы сделать это, создать системную переменную среды с именем «Путь к КЛАССУ»

<a name="external-library"></a>

## <a name="external-library"></a>Внешняя библиотека

В SQL Server 2019 CTP 2.4 внешние библиотеки можно использовать для языка Java в Windows и Linux. Те же функциональные возможности будут доступны на платформе Linux в следующей CTP-версии. Можно скомпилировать свои классы в JAR-файл и отправить JAR-файл и другие зависимости в базу данных при помощи [CREATE EXTERNAL LIBRARY](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql) DDL.

Пример того, как отправить JAR-файл с помощью внешней библиотеки.

```sql 
CREATE EXTERNAL LIBRARY myJar
FROM (CONTENT = '<local path to .jar file>') 
WITH (LANGUAGE = 'Java'); 
GO
```

Создание внешней библиотеки, не нужно предоставить [classpath](#classpath) в вызове sp_execute_external_script. SQL Server автоматически будет иметь доступ к классам Java и вы не обязательно для задания специальных разрешений для пути к классам.

Пример вызова метода в классе из пакета отправить в виде внешней библиотеки:

```sql
EXEC sp_execute_external_script
  @language = N'Java'
, @script = N'MyPackage.MyCLass.myMethod'
, @input_data_1 = N'SELECT * FROM MYTABLE'
with result sets ((column1 int))
```

Дополнительные сведения см. в разделе [CREATE EXTERNAL LIBRARY](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql).

## <a name="class-requirements"></a>Класс требования

Чтобы SQL Server для взаимодействия со средой выполнения Java необходимо реализовать статические переменные, определенные в классе. SQL Server затем можно выполнить метод в класс и exchange данных Java с помощью расширения языка Java.

> [!Note]
> Ожидается, что сведения о реализации для изменения в следующую CTP, поскольку мы работаем над повысить производительность разработчиков.

## <a name="method-requirements"></a>Требования к методу
Чтобы передать аргументы, используйте @param параметра в sp_execute_external_script. Сам метод не может иметь аргументов. Тип возвращаемого значения должен быть void.  

```java
public static void test()  {}
```

## <a name="data-inputs"></a>Входные данные 

В этом разделе объясняется, как передавать данные из запроса SQL Server с помощью Java **InputDataSet** в sp_execute_external_script.

Для каждого входного столбца, отправляет запрос SQL в Java необходимо объявить массив.

### <a name="inputdatacol"></a>inputDataCol

В текущей версии расширения Java **inputDataColN** переменная является обязательной, где *N* номер столбца. 

```java
public static <type>[] inputDataColN = new <type>[1]
```

Такие массивы нужно инициализировать (размер массива должен быть больше 0 и не отражать фактическую длину столбца).

Пример: `public static int[] inputDataCol1 = new int[1];`

Эти переменные массив будет заполняться входных данных из SQL server-запрос перед выполнением программы Java вы вызываете.

### <a name="inputnullmap"></a>inputNullMap

NULL карты используется модулем знать, какие значения имеют значение null. Этой переменной будут заполнены данными о значения null по SQL Server перед выполнением функции пользователя.

Пользователь должен только для инициализации этой переменной (и размер массива должен быть больше 0).

```java
public static boolean[][] inputNullMap = new boolean[1][1];
```

## <a name="data-outputs"></a>Выходные данные

В этом разделе описываются **OutputDataSet**, выходных наборов данных, возвращаемых из Java, которые можно отправить и сохранять в SQL Server.

> [!Note]
> Выходные параметры в [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) не поддерживаются в этой версии.

### <a name="outputdatacoln"></a>outputDataColN

Аналогичную **inputDataSet**, для каждого выходного столбца, приложение Java отправляет в SQL Server, необходимо объявить переменную массива. Все **outputDataCol** массивы должны иметь одинаковую длину. Необходимо убедиться, что это инициализируется к моменту завершения выполнения класса.

```java
public static <type>[] outputDataColN = new <type>[]
```

### <a name="numberofoutputcols"></a>numberofOutputCols

Значение этой переменной количество выходных столбцов данных, ожидается, что по завершении выполнения функции user.

```java
public static short numberofOutputCols = <expected number of output columns>;
```

### <a name="outputnullmap"></a>outputNullMap

NULL карты используется модулем для указания значения, которые имеют значение null. Это требуется, так как типы-примитивы не поддерживает значение null. В настоящее время мы также потребовать null карты для строковых типов, несмотря на то, что строки могут быть null. Значения NULL обозначаются «true».

Этот NullMap должны устанавливаться с ожидаемым количеством столбцов и строк, который возвращается в SQL Server.

```java
public static boolean[][] outputNullMap
```

## <a name="next-steps"></a>Следующие шаги

+ [Пример Java в SQL Server](java-first-sample.md)
+ [Типы данных Java и SQL Server](java-sql-datatypes.md)
+ [Расширение языка Java в SQL Server](extension-java.md)
