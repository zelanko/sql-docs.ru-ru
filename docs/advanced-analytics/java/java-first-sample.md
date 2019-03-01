---
title: Пример Java и руководство по SQL Server 2019 - службы машинного обучения SQL Server
description: Запустите пример кода Java на SQL Server 2019 дополнительные действия по использованию расширения языка Java с данными SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 02/28/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 86a379191033f49ab6a5d06ceda2d1ed7a747c12
ms.sourcegitcommit: 2533383a7baa03b62430018a006a339c0bd69af2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/01/2019
ms.locfileid: "57018040"
---
# <a name="sql-server-java-sample-walkthrough"></a>Пошаговое руководство по примеру SQL Server Java

В этом примере демонстрируется класс Java, который получает два столбца ("ID" и "text") из SQL Server и возвращает два столбца в SQL Server (идентификатор и ngram). Для строки сочетания и заданным Идентификатором код создает перестановки n-грамм (подстроки), возвращая перестановки вместе с исходного идентификатора. Длина ngram определяется параметр, переданный в класс Java.

## <a name="prerequisites"></a>предварительные требования

+ Экземпляр ядра СУБД SQL Server 2019 г. с помощью расширения среды .NET framework и программирования расширение Java [на Windows](../install/sql-machine-learning-services-windows-install.md) или [в Linux](https://docs.microsoft.com/sql/linux/sql-server-linux-setup). Дополнительные сведения о конфигурации системы, см. в разделе [расширение языка Java в SQL Server 2019](extension-java.md). Дополнительные сведения о написании кода для требования, см. в разделе [вызов Java в SQL Server](howto-call-java-from-sql.md).

+ SQL Server Management Studio или другое средство для выполнения T-SQL.

+ Java SE Development Kit (JDK) версии 8 в Windows или Linux.

Компиляции из командной строки с помощью **javac** достаточно для этого руководства. 

## <a name="1---load-sample-data"></a>1 - Загрузка образца данных

Во-первых, создайте и заполните *просматривает* таблицы с **идентификатор** и **текст** столбцов. Подключение к SQL Server и выполните следующий скрипт, чтобы создать таблицу:

```sql
DROP TABLE IF exists reviews;
GO
CREATE TABLE reviews(
    id int NOT NULL,
    "text" nvarchar(30) NOT NULL)

INSERT INTO reviews(id, "text") VALUES (1, 'AAA BBB CCC DDD EEE FFF')
INSERT INTO reviews(id, "text") VALUES (2, 'GGG HHH III JJJ KKK LLL')
INSERT INTO reviews(id, "text") VALUES (3, 'MMM NNN OOO PPP QQQ RRR')
GO
```

## <a name="2---class-ngramjava"></a>2 - Ngram.java класс

Начните с создания основного класса. Это первая из трех классов.

На этом шаге, создайте класс с именем **Ngram.java** и скопируйте приведенный ниже код Java с использованием этого файла. 


```java
//We will package our classes in a package called pkg
//Packages are option in Java-SQL, but required for this sample.
package pkg;

import java.util.List;
import java.util.stream.Collectors;
import java.util.stream.IntStream;

public class Ngram {

    //Required: This is only required if you are passing data in @input_data_1
    //from SQL Server in sp_execute_external_script
    public static int[] inputDataCol1 = new int[1];
    public static String[] inputDataCol2 = new String[1];

    //Required: Input null map. Size just needs to be set to "1"
    public static boolean[][] inputNullMap = new boolean[1][1];

    //Required: Output data columns returned back to SQL Server
    public static int[] outputDataCol1;
    public static String[] outputDataCol2;

    //Required: Output null map. Is populated with true or false values 
    //to indicate nulls
    public static boolean[][] outputNullMap;

    //Optional: This is only required if parameters are passed with @params
    // from SQL Server in sp_execute_external_script
    // n is giving us the size of ngram substrings
    public static int param1;

    //Optional: The number of rows we will be returning
    public static int numberOfRows;

    //Required: Number of output columns returned
    public static short numberOfOutputCols;

    /*Java main method - Only for testing purposes outside of SQL Server
    public static void main(String... args) {
        //getNGrams();
    }*/

    //This is the method we will be calling from SQL Server
    public static void getNGrams() {

        System.out.println("inputDataCol1.length= "+ inputDataCol1.length);
        if (inputDataCol1.length == 0 ) {
            // TODO: Set empty return
            return;
        }
        //Using a stream to "loop" over the input data inputDataCol1.length. You can also use a for loop for this.
        final List<InputRow> inputDataSet = IntStream.range(0, inputDataCol1.length)
                .mapToObj(i -> new InputRow(inputDataCol1[i], inputDataCol2[i]))
                .collect(Collectors.toList());


        //Again, we are using a stream to loop over data
        final List<OutputRow> outputDataSet = inputDataSet.stream()
                // Generate ngrams of size n for each incoming string
                // Each invocation of ngrams returns a list. flatMap flattens
                // the resulting list-of-lists to a flat list.
                .flatMap(inputRow -> ngrams(param1, inputRow.text).stream().map(s -> new OutputRow(inputRow.id, s)))
                .collect(Collectors.toList());

        //Print the outputDataSet
        System.out.println(outputDataSet);

        //Set the number of rows and columns we will be returning
        numberOfOutputCols = 2;
        numberOfRows = outputDataSet.size();
        outputDataCol1 = new int[numberOfRows]; // ID column
        outputDataCol2 = new String[numberOfRows]; //The ngram column
        outputNullMap = new boolean[2][numberOfRows];// output null map

        //Since we don't have any null values, we will populate all values in the outputNullMap to false
        IntStream.range(0, numberOfRows).forEach(i -> {
            final OutputRow outputRow = outputDataSet.get(i);
            outputDataCol1[i] = outputRow.id;
            outputDataCol2[i] = outputRow.ngram;
            outputNullMap[0][i] = false;
            outputNullMap[1][i] = false;
        });
    }

    // Example: ngrams(3, "abcde") = ["abc", "bcd", "cde"].
    private static List<String> ngrams(int n, String text) {
        return IntStream.range(0, text.length() - n + 1)
                .mapToObj(i -> text.substring(i, i + n))
                .collect(Collectors.toList());
    }
}
```

## <a name="3---class-inputrowjava"></a>3 - InputRow.java класс

Создайте второй класс с именем **InputRow.java**, состоящие из следующий код и сохранен в том же расположении, как **Ngram.java**.

```java
package pkg;

//This object represents one input row
public class InputRow {
    public final int id;
    public final String text;

    public InputRow(final int id, final String text) {
        this.id = id;
        this.text = text;
    }
}
```

## <a name="4---class-outputrowjava"></a>4 - OutputRow.java класс

Класс третьей и последней называется **OutputRow.java**. Скопируйте код и сохраните под OutputRow.java там же, что и остальные.

```java
package pkg;

//This object represents one output row
public class OutputRow {
    public final int id;
    public final String ngram;

    public OutputRow(final int id, final String ngram) {
        this.id = id;
        this.ngram = ngram;
    }

    @Override
    public String toString() { return id + ":" + ngram; }
}
```

## <a name="5---compile"></a>5 - компиляции

При наличии ваши классы все будет готово, запустите javac, чтобы скомпилировать их в файлы «.class» (`javac Ngram.java InputRow.java OutputRow.java`). Вы должны получить три файла .class для этого примера (Ngram.class InputRow.class и OutputRow.class).

Поместите скомпилированный код в подпапку с именем «pkg» в расположении, путь к классу. Если вы работаете на рабочей станции разработки, этот шаг можно, где скопируйте файлы на компьютер SQL Server.

Путь к классу — расположение скомпилированного кода. Например, в Linux, если путь к классу «/ home/myclasspath /», а затем .class файлы должны находиться в «/ home/myclasspath/pkg». В примере скрипта на шаге 7, пути к КЛАССАМ в sp_execute_external_script — «/ home/myclasspath /» (при условии, что Linux). 

В Windows, рекомендуется использовать относительно неполных папку структуры, одного или двух уровней, чтобы упростить разрешения. Например путь к классу может выглядеть «C:\myJavaCode» с вложенной папке \pkg содержащий скомпилированные классы. 

Дополнительные сведения о пути к классам, см. в разделе [задать путь к КЛАССУ](howto-call-java-from-sql.md#set-classpath). 

### <a name="using-jar-files"></a>С помощью JAR-файлы

Если вы планируете упаковки классов и зависимости в JAR-файлы, укажите полный путь к JAR-файлу в параметр CLASSPATH sp_execute_external_script. Например, если JAR-файл называется «ngram.jar», путь к КЛАССУ будет "/ home/myclasspath/ngram.jar" в Linux.

## <a name="6---set-permissions"></a>6 - Установка разрешений

Выполнение скрипта завершается успешно, только если удостоверения процесса нет доступа к коду. 

### <a name="on-linux"></a>В Linux

Предоставьте разрешения на чтение и выполнение на путь к классу **mssql_satellite** пользователя.

### <a name="on-windows"></a>В Windows

Предоставить разрешения «Чтение и выполнение» **SQLRUserGroup** и **все пакеты приложений** SID в папку, содержащую ваш скомпилированный код Java. 

Полное дерево необходимо иметь разрешения, от корня к последнему родительских во вложенную папку. 
 
1. Щелкните правой кнопкой мыши папку (например, «C:\myJavaCode»), выберите **свойства** > **безопасности**.
2. Нажмите кнопку **Изменить**.
3. Нажмите кнопку **Добавить**.
4. В **Выбор пользователей, компьютеров, учетных записей служб или групп**:
   + Нажмите кнопку **типы объектов** и убедитесь, что *принципы встроенных средств безопасности* и *группы* выбраны.
   + Нажмите кнопку **расположения** выберите имя локального компьютера в верхней части списка.
5. Введите **SQLRUserGroup**, проверьте имя и нажмите кнопку ОК, чтобы добавить в группу.
6. Введите **все ПАКЕТЫ ПРИЛОЖЕНИЙ**, проверьте имя и нажмите кнопку ОК, чтобы добавить. Если имя не разрешается, вернитесь на шаге расположения. Идентификатор безопасности — локально на вашем компьютере.

Убедитесь, что оба идентификатора безопасности иметь разрешения «Чтение и выполнение» на «pkg» вложенная папка и папка.

<a name="call-method"></a>

## <a name="7---call-getngrams"></a>7 - вызов *getNgrams()*

Чтобы вызвать код из SQL Server, укажите метод Java **getNgrams()** в параметре «скрипт» sp_execute_external_script. Этот метод принадлежит пакета, который называется «pkg» и файл класса с именем **Ngram.java**.

В этом примере передает параметр CLASSPATH для предоставления пути к файлам Java. Он также использует для передачи параметра к классу Java «params». Убедитесь, что этот путь к классам не превышает 30 символов. Если Да, увеличьте значение в приведенном ниже сценарии.

+ В Linux выполните следующий код в SQL Server Management Studio или другого средства, используемые для запуска Transact-SQL. 

+ В Windows, измените @myClassPath для N'C:\myJavaCode\' (предполагается, что это родительская папка \pkg) перед выполнением запроса в SQL Server Management Studio или другого средства.

```sql
DECLARE @myClassPath nvarchar(50)
DECLARE @n int 
--This is where you store your classes or jars.
--Update this to your own classpath
SET @myClassPath = N'/home/myclasspath/'
--This is the size of the ngram
SET @n = 3
EXEC sp_execute_external_script
  @language = N'Java'
, @script = N'pkg.Ngram.getNGrams'
, @input_data_1 = N'SELECT id, text FROM reviews'
, @parallel = 0
, @params = N'@CLASSPATH nvarchar(30), @param1 INT'
, @CLASSPATH = @myClassPath
, @param1 = @n
with result sets ((ID int, ngram varchar(20)))
GO
```

### <a name="results"></a>Результаты

После выполнения вызова, вы должны получить результирующий набор показывает два столбца:

![Полученный в результате пример Java](../media/java/java-sample-results.png "пример результатов")

### <a name="if-you-get-an-error"></a>Если отобразится сообщение об ошибке

Исключить возможные проблемы, связанные с пути к классам. 

+ Путь к классу должен состоять из родительской папки и вложенные папки, но не вложенной папке «pkg». Хотя вложенная папка pkg должен существовать, он не должен быть в пути к классам значение, указанное в хранимой процедуре.

+ Во вложенную папку «pkg» должен содержать скомпилированный код для всех трех классов.

+ Длина пути к классам, не может превышать объявленное значение (`DECLARE @myClassPath nvarchar(50)`). В этом случае путь будет усечено до первые 50 символов и не будет загружен в скомпилированный код. Можно сделать `SELECT @myClassPath` для проверки значения. Увеличение длины, если недостаточно 50 символов. 

+ Наконец, проверьте разрешения на *каждого* папки из корневой папки во вложенную папку «pkg», чтобы убедиться, что идентификаторы безопасности, запуск внешнего процесса имеет разрешения на чтение и выполнение кода.

## <a name="see-also"></a>См. также

+ [Как вызвать Java в SQL Server](howto-call-java-from-sql.md)
+ [Расширения Java в SQL Server](extension-java.md)
+ [Типы данных Java и SQL Server](java-sql-datatypes.md)
