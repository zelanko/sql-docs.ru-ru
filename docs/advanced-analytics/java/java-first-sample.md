---
title: Пример Java и руководство по SQL Server 2019 - службы машинного обучения SQL Server
description: Запустите пример кода Java на SQL Server 2019 дополнительные действия по использованию расширения языка Java с данными SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/23/2019
ms.topic: conceptual
author: nelgson
ms.author: negust
ms.reviewer: dphansen
manager: cgronlun
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 000318716b07f58e94bd5c482d9c349e5d4e5481
ms.sourcegitcommit: bd5f23f2f6b9074c317c88fc51567412f08142bb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2019
ms.locfileid: "63473764"
---
# <a name="sql-server-regex-java-sample"></a>Пример регулярного выражения Java SQL Server

В этом примере демонстрируется класс Java, который получает два столбца ("ID" и "text") из SQL Server, а также использует регулярное выражение в качестве входного параметра. Класс возвращает два столбца в SQL Server ("ID" и "text").

Для заданного текста в текстовый столбец, отправленных к классу Java код проверяет, если выполняется регулярному выражению и возвращает этот текст, вместе с исходного идентификатора. 

В данном конкретном примере используется регулярное выражение, которое проверяет, если текст содержит слово «Java» или «java».

## <a name="microsoft-extensibility-sdk-for-java-for-microsoft-sql-server"></a>Расширения Microsoft SDK для Java для Microsoft SQL Server

 В CTP-версии 2.5 мы изменяем способы реализации кода Java, который использует расширение языка Java для взаимодействия с SQL Server. Это позволит обеспечить удобство работы разработчиков при взаимодействии с SQL Server из Java.

Как вспомогательный интерфейс, что сделает его проще реализовать код Java, выполняемый в SQL Server, следует подумать о пакете SDK.

> [!NOTE]
> Внедрение пакета SDK — большой шаг вперед для предыдущих CTP-версий. Все предыдущие примеры, необходимо было работы потребуется обновить для использования пакета SDK.

Дополнительные сведения см. в разделе [документации по пакету SDK](java-sdk.md).

## <a name="prerequisites"></a>предварительные требования

+ Экземпляр ядра СУБД SQL Server 2019 г. с помощью расширения среды .NET framework и программирования расширение Java [на Windows](../install/sql-machine-learning-services-windows-install.md) или [в Linux](https://docs.microsoft.com/sql/linux/sql-server-linux-setup). Дополнительные сведения о конфигурации системы, см. в разделе [расширение языка Java в SQL Server 2019](extension-java.md). Дополнительные сведения о написании кода для требования, см. в разделе [вызов Java в SQL Server](howto-call-java-from-sql.md).

+ SQL Server Management Studio или Azure Data Studio для выполнения T-SQL.

+ Java SE Development Kit (JDK) 8 или JRE 8 в Windows или Linux.

+ [Пакет SDK расширения Microsoft Java для Microsoft SQL Server](http://aka.ms/mssql-java-lang-extension) mssql-java-lang-extension.jar.

Компиляции из командной строки с помощью **javac** достаточно для этого руководства.

## <a name="1---create-sample-data-in-a-sql-server-table"></a>1 - Создание демонстрационных данных в таблицу SQL Server

Во-первых, создайте и заполните *testdata* таблицы с **идентификатор** и **текст** столбцов. Подключение к SQL Server и выполните следующий скрипт, чтобы создать таблицу:

```sql
CREATE DATABASE javatest
GO
USE javatest
GO

-- Create table for test data
DROP TABLE IF exists testdata;
GO

CREATE TABLE testdata(
id int NOT NULL,
"text" nvarchar(100) NOT NULL)
GO

TRUNCATE TABLE testdata
GO

-- Insert data into test table
INSERT INTO testdata(id, "text") VALUES (1, 'This sentence contains java')
INSERT INTO testdata(id, "text") VALUES (2, 'This sentence does not')
INSERT INTO testdata(id, "text") VALUES (3, 'I love Java!')
GO
Select * FROM testdata
```

## <a name="2---class-regexsamplejava"></a>2 - RegexSample.java класс

Начните с создания основного класса.

На этом шаге, создайте класс с именем **RegexSample.java** и скопируйте приведенный ниже код Java с использованием этого файла.

Это основной класс в настоящее время импортирует пакет SDK, что означает, что JAR-файл, Скачанный в шаге 1 должен быть обнаруживаемыми от этого класса.

> [!NOTE]
> Обратите внимание на то, что этот класс импортирует пакет расширений пакета SDK для Java.
См. в статье [Microsoft расширяемости SDK для Java для Microsoft SQL Server](java-sdk.md) для получения дополнительных сведений.

```java
package pkg;

import com.microsoft.sqlserver.javalangextension.PrimitiveDataset;
import com.microsoft.sqlserver.javalangextension.AbstractSqlServerExtensionExecutor;
import java.util.LinkedHashMap;
import java.util.LinkedList;
import java.util.ListIterator;
import java.util.regex.*;

public class RegexSample extends AbstractSqlServerExtensionExecutor {
    private Pattern expr;

    public RegexSample() {
        // Setup the expected extension version, and class to use for input and output dataset
        executorExtensionVersion = SQLSERVER_JAVA_LANG_EXTENSION_V1;
        executorInputDatasetClassName = PrimitiveDataset.class.getName();
        executorOutputDatasetClassName = PrimitiveDataset.class.getName();
    }
    
    public PrimitiveDataset execute(PrimitiveDataset input, LinkedHashMap<String, Object> params) {
        // Validate the input parameters and input column schema
        validateInput(input, params);

        int[] inIds = input.getIntColumn(0);
        String[] inValues = input.getStringColumn(1);
        int rowCount = inValues.length;

        String regexExpr = (String)params.get("regexExpr");
        expr = Pattern.compile(regexExpr);

        System.out.println("regex expression: " + regexExpr);

        // Lists to store the output data
        LinkedList<Integer> outIds = new LinkedList<Integer>();
        LinkedList<String> outValues = new LinkedList<String>();

        // Evaluate each row
        for(int i = 0; i < rowCount; i++) {
            if (check(inValues[i])) {
                outIds.add(inIds[i]);
                outValues.add(inValues[i]);
            }
        }

        int outputRowCount = outValues.size();

        int[] idOutputCol = new int[outputRowCount];
        String[] valueOutputCol = new String[outputRowCount];

        // Convert the list of output columns to arrays
        outValues.toArray(valueOutputCol);

        ListIterator<Integer> it = outIds.listIterator(0);
        int rowId = 0;

        System.out.println("Output data:");
        while (it.hasNext()) {
            idOutputCol[rowId] = it.next().intValue();

            System.out.println("ID: " + idOutputCol[rowId] + " Value: " + valueOutputCol[rowId]);
            rowId++;
        }

        // Construct the output dataset
        PrimitiveDataset output = new PrimitiveDataset();

        output.addColumnMetadata(0, "ID", java.sql.Types.INTEGER, 0, 0);
        output.addColumnMetadata(1, "Text", java.sql.Types.NVARCHAR, 0, 0);

        output.addIntColumn(0, idOutputCol, null);
        output.addStringColumn(1, valueOutputCol);

        return output;
    }

    private void validateInput(PrimitiveDataset input, LinkedHashMap<String, Object> params) {
        // Check for the regex expression input parameter
        if (params.get("regexExpr") == null) {
            throw new IllegalArgumentException("Input parameter 'regexExpr' is not found");
        }

        // The expected input schema should be at least 2 columns, (INTEGER, STRING)
        if (input.getColumnCount() < 2) {
            throw new IllegalArgumentException("Unexpected input schema, schema should be an (INTEGER, NVARCHAR or VARCHAR)");
        }

        // Check that the input column types are expected
        if (input.getColumnType(0) != java.sql.Types.INTEGER &&
                (input.getColumnType(1) != java.sql.Types.VARCHAR && input.getColumnType(1) == java.sql.Types.NVARCHAR )) {
            throw new IllegalArgumentException("Unexpected input schema, schema should be an (INTEGER, NVARCHAR or VARCHAR)");
        }
    }

    private boolean check(String text) {
        Matcher m = expr.matcher(text);

        return m.find();
    }
}
```

## <a name="3-compile-and-create-jar-file"></a>3 скомпилировать и создать JAR-файл

Мы рекомендуем упаковке классы и зависимости в JAR-файлы. Большинство сред IDE Java, такая как Eclipse или IntelliJ поддержки Создание JAR-файлы, когда вы сборки и скомпилировать проект. В этом примере мы назовем JAR-файл **regex.jar**.

Можно вручную при создании JAR-файл, выполните действия, см. в разделе [Создание JAR-файл](extension-java.md#create-jar).

> [!NOTE]
> Этот образец использует пакеты, это означает, что пакет «pkg», заданному в верхней части класса гарантирует, что скомпилированный код сохраняется в вложенную папку с именем «pkg». Это автоматически при использовании интегрированной среды разработки, но при компиляции с помощью классов вручную **javac**, вам потребуется разместить скомпилированного кода в папке sub pkg вручную.

## <a name="4---create-external-libraries"></a>4 - Создание внешних библиотек

Создание внешней библиотеки, SQL Server автоматически получают доступ к файлам jar, и вы не обязательно для задания специальных разрешений для пути к классам.

В этом примере необходимо создать два внешних библиотек. Один для пакета SDK и один для примера кода Java регулярное выражение.

1.  Скачайте [Microsoft расширяемости SDK для Java для Microsoft SQL Server](http://aka.ms/mssql-java-lang-extension) mssql-java-lang-extension.jar.

1. Создание внешней библиотеки для пакета sdk

```sql
-- Create external library for the SDK
CREATE EXTERNAL LIBRARY sdk
FROM (CONTENT = '<path>/mssql-java-lang-extension.jar')
WITH (LANGUAGE = 'Java');
GO
```

3. Создание внешней библиотеки пример регулярного выражения

```sql
-- Create external library for the regex sample
CREATE EXTERNAL LIBRARY regex
FROM (CONTENT = '<path>/regex.jar')
WITH (LANGUAGE = 'Java');
GO
```

## <a name="5---set-permissions-skip-if-you-performed-step-4"></a>5 - разрешения (пропустить, если вы выполнили шаг 4)

Этот шаг не требуется, если вы используете внешние библиотеки. Рекомендуемый способ работы является создание внешней библиотеки из вы JAR-файл.

Если вы не хотите использовать внешние библиотеки, вам потребуется задать необходимые разрешения. Выполнение скрипта завершается успешно, только если удостоверения процесса нет доступа к коду. Можно найти дополнительные сведения об установке разрешений [здесь](extension-java.md).

### <a name="on-linux"></a>В Linux

Предоставьте разрешения на чтение и выполнение на путь к классу **mssql_satellite** пользователя.

### <a name="on-windows"></a>В Windows

Предоставить разрешения «Чтение и выполнение» **SQLRUserGroup** и **все пакеты приложений** SID в папку, содержащую ваш скомпилированный код Java. 

Полное дерево необходимо иметь разрешения, от корневого родителя к последней вложенной папки. 
 
1. Щелкните правой кнопкой мыши папку (например, «C:\myJavaCode»), выберите **свойства** > **безопасности**.
2. Нажмите кнопку **Изменить**.
3. Нажмите кнопку **Добавить**.
4. В **Выбор пользователей, компьютеров, учетных записей служб или групп**:
   + Нажмите кнопку **типы объектов** и убедитесь, что *принципы встроенных средств безопасности* и *группы* выбраны.
   + Нажмите кнопку **расположения** выберите имя локального компьютера в верхней части списка.
5. Введите **SQLRUserGroup**, проверьте имя и нажмите кнопку ОК, чтобы добавить в группу.
6. Введите **все ПАКЕТЫ ПРИЛОЖЕНИЙ**, проверьте имя и нажмите кнопку ОК, чтобы добавить. Если имя не разрешается, вернитесь на шаге расположения. Идентификатор безопасности — локально на вашем компьютере.

Убедитесь, что оба идентификатора безопасности иметь разрешения «Чтение и выполнение» на «pkg» вложенную папку и папка.

<a name="call-method"></a>

## <a name="2---call-the-java-class"></a>2 - вызвать класс Java

Чтобы вызвать код Java из SQL Server, мы создадим хранимую процедуру, которая вызывает sp_execute_external_script. В параметре «скрипт» мы определим, какой [пакет]. [class] требуется вызвать. В этом примере класс принадлежит к пакету, вызываемому **pkg** и файл класса с именем **RegexSample.java**.

> [!NOTE]
>Мы не применяется частное определение вызываемый метод. По умолчанию **выполнение** метод будет вызываться. Это означает необходимость выполните интерфейс SDK и реализации метода execute в класс Java, если вы хотите иметь возможность вызвать класс из SQL Server.

```sql
/*
This stored procedure takes an input query (input dataset) and a regular expression and returns the rows that fulfilled the given regular expression. This sample uses a regular expression that checks if a text contains the word "Java" or "java" ([Jj]ava) 
*/

CREATE OR ALTER PROCEDURE [dbo].[java_regex] @expr nvarchar(200), @query nvarchar(400)
AS
BEGIN
--Call the Java program by giving the package.className in @script
--The method invoked in the Java code is always the "execute" method
EXEC sp_execute_external_script
  @language = N'Java'
, @script = N'pkg.RegexSample'
, @input_data_1 = @query
, @params = N'@regexExpr nvarchar(200)'
, @regexExpr = @expr
with result sets ((ID int, text nvarchar(100)));
END
GO

--Now execute the above stored procedure and provide the regular expression and an input query
EXECUTE [dbo].[java_regex] N'[Jj]ava', N'SELECT id, text FROM testdata'
GO
```

### <a name="results"></a>Результаты

После выполнения вызова, вы должны получить результирующий набор с две строки.

![Полученный в результате пример Java](../media/java/java-sample-results.png "пример результатов")

### <a name="if-you-get-an-error"></a>Если отобразится сообщение об ошибке

+ При компиляции классов, вложенную папку «pkg» должен содержать скомпилированный код для всех трех классов.

+ Наконец, если вы не используете внешние библиотеки, проверьте разрешения на *каждого* папки из корневой папки для вложенной папки «pkg», чтобы убедиться, что идентификаторы безопасности, запуск внешнего процесса имеет разрешения на чтение и выполнение кода.

## <a name="next-steps"></a>Следующие шаги

+ [Расширения Microsoft SDK для Java для Microsoft SQL Server](java-sdk.md)
+ [Как вызвать Java в SQL Server](howto-call-java-from-sql.md)
+ [Расширения Java в SQL Server](extension-java.md)
+ [Типы данных Java и SQL Server](java-sql-datatypes.md)
