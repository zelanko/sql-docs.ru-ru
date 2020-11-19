---
title: Руководство по Поиск строк с использованием регулярных выражений в Java
description: В этом руководстве показано, как использовать расширения языка SQL Server и выполнять код Java, который осуществляет поиск строки с использованием регулярных выражений (regex).
author: dphansen
ms.author: davidph
ms.date: 11/05/2019
ms.topic: tutorial
ms.prod: sql
ms.technology: language-extensions
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 21d981c75881d0d971b0f27757015792237f12e3
ms.sourcegitcommit: 82b92f73ca32fc28e1948aab70f37f0efdb54e39
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2020
ms.locfileid: "94870150"
---
# <a name="tutorial-search-for-a-string-using-regular-expressions-regex-in-java"></a>Руководство по Поиск строки с использованием регулярных выражений (regex) в Java
[!INCLUDE [SQL Server 2019 and later](../../includes/applies-to-version/sqlserver2019.md)]

В этом руководстве показано, как использовать [расширения языка SQL Server](../language-extensions-overview.md) и создать класс Java, принимающий два столбца (идентификатор и текст) из SQL Server и регулярное выражение (regex) в качестве входного параметра. Класс возвращает в SQL Server два столбца (идентификатор и текст).

Для заданного текста в текстовом столбце, отправленном в класс Java, код проверяет, выполнено ли данное регулярное выражение, и возвращает этот текст вместе с исходным идентификатором.

В данном примере кода используется регулярное выражение, которое проверяет, содержит ли текст слово "Java" или "java".

## <a name="prerequisites"></a>Предварительные требования

+ Экземпляр ядра СУБД SQL Server 2019 с платформой расширяемости и расширением программирования Java [в Windows](../install/windows-java.md) или [в Linux](../../linux/sql-server-linux-setup-language-extensions-java.md). Дополнительные сведения см. в статье [Расширения языка в SQL Server 2019](../language-extensions-overview.md). Дополнительные сведения о требованиях к программированию см. в разделе [Как вызывать Java в SQL Server](../how-to/call-java-from-sql.md).

+ SQL Server Management Studio или Azure Data Studio для выполнения T-SQL.

+ Пакет SDK для Java SE (JDK) 8 или JRE 8 в Windows или Linux.

+ Файл **mssql-java-lang-extension.jar** из [пакета SDK для расширения возможностей Java в Microsoft SQL Server](../how-to/extensibility-sdk-java-sql-server.md).

Для работы с этим руководством достаточно компиляции из командной строки с использованием **javac**.

## <a name="create-sample-data"></a>Создание примера набора данных

Сначала создайте новую базу данных и заполните таблицу **testdata** со столбцами **Идентификатор** и **Текст**.

```sql
CREATE DATABASE javatest
GO

USE javatest
GO

CREATE TABLE testdata (
    id int NOT NULL,
    "text" nvarchar(100) NOT NULL
)
GO

-- Insert data into test table
INSERT INTO testdata(id, "text") VALUES (1, 'This sentence contains java')
INSERT INTO testdata(id, "text") VALUES (2, 'This sentence does not')
INSERT INTO testdata(id, "text") VALUES (3, 'I love Java!')
GO
```

## <a name="create-the-main-class"></a>Создание основного класса

В этом шаге создайте файл класса с именем **RegexSample.java** и скопируйте в этот файл следующий код Java.

Этот основной класс импортирует пакет SDK — это значит, что JAR-файл, скачанный в шаге 1, должен быть доступен для обнаружения из этого класса.

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

## <a name="compile-and-create-a-jar-file"></a>Компиляция и создание JAR-файла

Упакуйте классы и зависимости в файлы `.jar`. Большинство IDE Java (например, Eclipse или IntelliJ) поддерживают создание файлов `.jar` при сборке или компиляции проекта. Присвойте файлу `.jar` имя **regex.jar**.

Если вы не используете IDE Java, можно вручную создать файл `.jar`. Дополнительные сведения см. в разделе [Как создать JAR-файл Java из файлов класса](../how-to/create-a-java-jar-file-from-class-files.md).

> [!NOTE]
> В этом учебнике используются пакеты. Строка `package pkg;` в верхней части класса гарантирует, что скомпилированный код будет сохранен во вложенной папке с именем **pkg**. Если используется IDE, скомпилированный код автоматически сохраняется в этой папке. Если используется **javac** для компиляции классов вручную, необходимо поместить скомпилированный код в папку **pkg**.

## <a name="create-external-language"></a>Создание внешнего языка

Необходимо создать внешний язык в базе данных. Внешний язык — это объект области базы данных. Это значит, что внешние языки, такие как Java, необходимо создавать для каждой базы данных, в которой вы хотите их использовать.

### <a name="create-external-language-on-windows"></a>Создание внешнего языка в Windows

Если вы пользуетесь Windows, выполните следующие действия, чтобы создать внешний язык для Java.

1. Создайте ZIP-файл, содержащий расширение.

    При установке SQL Server в операционной системе Windows **ZIP**-файл расширения Java устанавливается в этот каталог: `[SQL Server install path]\MSSQL\Binn\java-lang-extension.zip`. Этот ZIP-файл содержит **javaextension.dll**.

2. Создайте внешний язык Java из ZIP-файла:

    ```sql
    CREATE EXTERNAL LANGUAGE Java
    FROM
    (CONTENT = N'[SQL Server install path]\MSSQL\Binn\java-lang-extension.zip', FILE_NAME = 'javaextension.dll',
    ENVIRONMENT_VARIABLES = N'{"JRE_HOME":"<path to JRE>"}' );
    GO
    ```

### <a name="create-external-language-on-linux"></a>Создание внешнего языка в Linux

Во время установки **TAR/GA**-файл расширения сохраняется в этот каталог: `/opt/mssql-extensibility/lib/java-lang-extension.tar.gz`.

Чтобы создать внешний язык Java, выполните в Linux следующую инструкцию T-SQL:

```sql
CREATE EXTERNAL LANGUAGE Java
FROM (CONTENT = N'/opt/mssql-extensibility/lib/java-lang-extension.tar.gz', file_name = 'javaextension.so',
ENVIRONMENT_VARIABLES = N'{"JRE_HOME":"<path to JRE>"}' );
GO
```

### <a name="permissions-to-execute-external-language"></a>Разрешения на выполнение внешнего языка

Для выполнения кода Java пользователю необходимо предоставить разрешение на выполнение внешнего скрипта на этом языке.

Дополнительные сведения см. в разделе [CREATE EXTERNAL LANGUAGE](../../t-sql/statements/create-external-language-transact-sql.md).

## <a name="create-external-libraries"></a>Создание внешних библиотек

Для создания внешней библиотеки для файлов `.jar` используйте инструкцию [CREATE EXTERNAL LIBRARY](../../t-sql/statements/create-external-library-transact-sql.md). SQL Server получит доступ к файлам `.jar`, и вам не нужно задавать специальные разрешения на доступ к **каталогу классов**.

В этом примере будут созданы две внешние библиотеки: одна для пакета SDK, вторая для кода регулярных выражений Java.

1. JAR-файл пакета SDK **mssql-java-lang-extension.jar** устанавливается как часть SQL Server 2019 и в Windows, и в Linux.

    + Путь установки по умолчанию в Windows: **[домашний каталог установки экземпляра]\MSSQL\Binn\mssql-java-lang-extension.jar**

    + Путь установки по умолчанию в Linux: **/opt/mssql/lib/mssql-java-lang-extension.jar**

    Это открытый код, который можно найти в [репозитории расширений языка SQL Server в GitHub](https://github.com/microsoft/sql-server-language-extensions). Дополнительные сведения см. в разделе [Пакет SDK для расширения возможностей Java в Microsoft SQL Server](../how-to/extensibility-sdk-java-sql-server.md).

2. Создайте внешнюю библиотеку для пакета SDK.

    ```sql
    CREATE EXTERNAL LIBRARY sdk
    FROM (CONTENT = '<OS specific path from above>/mssql-java-lang-extension.jar')
    WITH (LANGUAGE = 'Java');
    GO
    ```

3. Создайте внешнюю библиотеку для кода RegEx.

    ```sql
    CREATE EXTERNAL LIBRARY regex
    FROM (CONTENT = '<path>/regex.jar')
    WITH (LANGUAGE = 'Java');
    GO
    ```

## <a name="set-permissions"></a>Установка разрешений

> [!NOTE]
> Пропустите этот шаг, если на предыдущем этапе вы использовали внешние библиотеки. Рекомендуемый способ — создать внешнюю библиотеку из файла `.jar`.

Если вы не хотите использовать внешние библиотеки, нужно будет задать необходимые разрешения. Скрипты выполняются успешно, только если удостоверения процессов имеют доступ к вашему коду. Дополнительные сведения о настройке разрешений см. в [руководстве по установке](../install/windows-java.md).

### <a name="on-linux"></a>В Linux

Предоставьте разрешения на чтение и выполнение для каталогов классов пользователю **mssql_satellite**.

### <a name="on-windows"></a>В Windows

Предоставьте разрешения на чтение и выполнение для **SQLRUserGroup** и индикаторов безопасности **всех пакетов приложений** в папке, содержащей скомпилированный вами код Java.

Все дерево, от корневого родительского каталога до последней вложенной папки, должно иметь разрешения.

1. Щелкните папку (например, `C:\myJavaCode`) правой кнопкой мыши и выберите **Свойства** > **Безопасность**.
2. Нажмите кнопку **Изменить**.
3. Нажмите кнопку **Добавить**.
4. В диалоговом окне **Выбор пользователей, компьютеров, учетных записей служб или групп**:
   1. Нажмите **Типы объектов** и убедитесь, что выбраны параметры *Встроенные принципы безопасности* и *Группы*.
   2. Нажмите **Расположения** и выберите имя локального компьютера в верхней части списка.
5. Введите **SQLRUserGroup**, проверьте имя и нажмите кнопку ОК, чтобы добавить группу.
6. Введите **ВСЕ ПАКЕТЫ ПРИЛОЖЕНИЙ**, проверьте имя и нажмите кнопку ОК для добавления. 
    Если имя разрешить не удается, верните к шагу "Расположения". Идентификатор безопасности является локальным для вашего компьютера.

Убедитесь, что оба удостоверения безопасности имеют разрешения на **Чтение и выполнение** для папки и вложенной папки **pkg**.

<a name="call-method"></a>

## <a name="call-the-java-class"></a>Вызов класса Java

Создайте хранимую процедуру, которая вызывает `sp_execute_external_script` для вызова кода Java из SQL Server. В параметре **script** укажите `package.class`, который требуется вызвать. В приведенном ниже коде класс принадлежит пакету с именем **pkg** и файлу класса с именем **RegexSample.java**.

> [!NOTE]
> Код не определяет, какой метод нужно вызывать. По умолчанию будет вызван метод **execute**. В связи с этим, чтобы иметь возможность вызывать класс из SQL Server, вам нужно следовать интерфейсу SDK и реализовать метод execute в классе Java.

Хранимая процедура принимает входной запрос (входной набор данных) и регулярное выражение и возвращает строки, которые выполнили данное регулярное выражение. В данном примере используется регулярное выражение `[Jj]ava`, которое проверяет, содержит ли текст слово **Java** или **java**.

```sql
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

После выполнения вызова необходимо получить результирующий набор с двумя строками.

![Результаты из примера для языка Java](../media/java/java-sample-results.png "Образец результатов")

### <a name="if-you-get-an-error"></a>Если возникла ошибка

+ При компиляции классов вложенная папка **pkg** должна содержать скомпилированный код для всех трех классов.

+ Если вы не используете внешние библиотеки, проверьте разрешения для *каждой* папки, начиная с **корневого каталога** и заканчивая папкой **pkg**, чтобы убедиться, что удостоверения безопасности, выполняющие внешний процесс, имеют разрешение на чтение и выполнение вашего кода.

## <a name="next-steps"></a>Дальнейшие действия

+ [Как вызвать код Java в SQL Server](../how-to/call-java-from-sql.md)
+ [Расширения Java в SQL Server](../language-extensions-overview.md)
+ [Типы данных Java и SQL Server](../how-to/java-to-sql-data-types.md)