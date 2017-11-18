---
title: "Использование адаптивной буферизации | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 92d4e3be-c3e9-4732-9a60-b57f4d0f7cb7
caps.latest.revision: 53
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 80944d5ebb5ec8c9f6ba98d9c520b10a0c4ade30
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="using-adaptive-buffering"></a>Использование адаптивной буферизации
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Адаптивная буферизация, разработана для получения любых данных большого объема без затрат на использование серверных курсоров. Приложения могут использовать функцию адаптивной буферизации со всеми версиями [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] , поддерживаемыми драйвером.  
  
 Как правило, когда [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] выполняет запрос, драйвер извлекает все результаты с сервера в память приложения. Несмотря на то, что такой подход позволяет минимизировать потребление ресурсов на [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], он может вызывать OutOfMemoryError в приложении JDBC для запросов, производящих слишком большие результаты.  
  
 Чтобы приложения могли обрабатывать результаты очень большого объема, [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] реализует адаптивную буферизацию. При адаптивной буферизации драйвер извлекает результаты выполнения инструкции из [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] как приложение должно их, а не все сразу. Драйвер также удаляет результаты, когда приложение теряет к ним доступ. Ниже приводятся примеры ситуаций, когда адаптивная буферизация может быть полезной.  
  
-   **Запрос создает очень большой результирующий набор:** приложение может выполнить инструкцию SELECT, возвращающую больше строк, чем может уместиться в памяти приложения. В предыдущих версиях приложение должно было использовать серверный курсор, чтобы избежать OutOfMemoryError. Адаптивная буферизация обеспечивает возможность однопроходного просмотра данных в режиме только для чтения для результирующего набора произвольно большого объема без использования курсора сервера.  
  
-   **Запрос создает очень большие**[SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md)**столбцы или**[SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md)**значения параметра OUT:**  Приложение может извлечь одно значение (столбец или параметр OUT) слишком большого объема, чтобы поместиться полностью в памяти приложения.         Адаптивная буферизация позволяет клиентскому приложению получать значения в виде потока, с помощью методов getCharacterStream, getBinaryStream или getAsciiStream. Приложение извлекает значение из [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] при чтении из потока.  
  
> [!NOTE]  
>  Благодаря адаптивной буферизации драйвер JDBC помещает в буфер только необходимое количество данных. Драйвер не позволяет любому открытому методу контролировать или ограничивать размер буфера.  
  
## <a name="setting-adaptive-buffering"></a>Настройка адаптивной буферизации  
 Начиная с драйвера JDBC версии 2.0, драйвер поведение по умолчанию — "**адаптивный**». Другими словами, чтобы получить адаптивное поведение буферизации, приложению не нужно запрашивать адаптивное поведение явным образом. В версии 1.2, однако использовался режим буферизации «**полного**» по умолчанию и приложение должно было запросить режим адаптивной буферизации явным образом.  
  
 Существуют три способа, с помощью которых приложение может запросить выполнение адаптивной буферизации.  
  
-   Приложение может задать свойство соединения **responseBuffering** значение «adaptive». Дополнительные сведения о настройке свойств соединения см. в разделе [задание свойств соединения](../../connect/jdbc/setting-the-connection-properties.md).  
  
-   Приложение может использовать [setResponseBuffering](../../connect/jdbc/reference/setresponsebuffering-method-sqlserverdatasource.md) метод [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md) объекта, чтобы задать режим буферизации ответов для всех подключений, созданных посредством [ SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md) объекта.  
  
-   Приложение может использовать [setResponseBuffering](../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md) метод [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) класса, чтобы задать режим буферизации ответов для определенного объекта инструкции.  
  
 При использовании драйвера JDBC версии 1.2 приложения должны были приводить объект инструкции к [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) класс, используемый [setResponseBuffering](../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md) метод. В примерах кода в [большой образец данных чтения](../../connect/jdbc/reading-large-data-sample.md) и [чтения больших объемов данных с помощью хранимых процедур образец](../../connect/jdbc/reading-large-data-with-stored-procedures-sample.md) показана эта устаревшая практика.  
  
 Тем не менее, с помощью драйвера JDBC версии 2.0, приложения могут использовать [isWrapperFor](../../connect/jdbc/reference/iswrapperfor-method-sqlserverstatement.md) метод и [unwrap](../../connect/jdbc/reference/unwrap-method-sqlserverstatement.md) метод доступа к функциям конкретного поставщика без необходимости о реализации иерархии класса. Пример кода см. в разделе [обновление большой образец данных](../../connect/jdbc/updating-large-data-sample.md) раздела.  
  
## <a name="retrieving-large-data-with-adaptive-buffering"></a>Извлечение данных большого объема при помощи адаптивной буферизации  
 Когда большие значения считываются в первый раз с помощью get\<типа > методы потока и столбцам ResultSet и параметрам CallableStatement OUT осуществляется в порядке, возвращенном [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], Адаптивная буферизация минимизирует приложения Использование памяти при обработке результатов. При использовании адаптивной буферизации происходит следующее.  
  
-   Get\<типа > потока методы, определенные в [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) и [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) классы возвращают потоки только для чтения по умолчанию, хотя потоки можно сбросить, если выделены приложением. Если приложению нужно `reset` потока, он должен вызывать `mark` метод, сначала потока.  
  
-   Get\<типа > потока методы, определенные в [SQLServerClob](../../connect/jdbc/reference/sqlserverclob-class.md) и [SQLServerBlob](../../connect/jdbc/reference/sqlserverblob-class.md) классы возвращают потоки, которые всегда можно переместить в исходное положение потока без вызов `mark` метод.  
  
 Если приложение использует адаптивную буферизацию, значения, извлекаемые get\<типа > поток методы могут быть извлечены только один раз. Если попытаться вызвать любой get\<типа > метод относительно того же столбца или параметра после вызова get\<типа > метод поток того же объекта исключения, исключение с сообщением, «данные уже был осуществлен и недоступен для этого столбец или параметр».  
  
> [!NOTE]
> Вызов ResultSet.close() в ходе обработки результирующий набор, потребуется включить драйвера Microsoft JDBC для SQL Server для чтения и отменить все оставшиеся пакеты. Это может занять немало времени, если запрос возвращает большой набор данных, и особенно в том случае, если используется медленное подключение к сети.     
  
## <a name="guidelines-for-using-adaptive-buffering"></a>Руководство по использованию адаптивной буферизации  
 Разработчики должны следовать данному руководству для минимизации использования памяти приложением.  
  
-   Старайтесь не использовать свойство строки соединения **selectMethod = cursor** разрешить приложению обработать слишком большой результирующий набор. Функция адаптивной буферизации позволяет приложениям обрабатывать очень большие однопроходные результирующие наборы, доступные только для чтения, без использования серверного курсора. Обратите внимание, что при установке **selectMethod = cursor**все однопроходный, затрагивает только для чтения результирующих наборов, формируемые этим подключением. Другими словами, если приложение рутинно обрабатывает короткие результирующие наборы с несколькими строками, создание, чтение и закрытие серверного курсора для каждого результирующего набора будет использовать больше ресурсов на стороне клиента и стороне сервера, чем в случае когда  **метод selectMethod** равно **курсор**.  
  
-   Считать с помощью методов getCharacterStream, getBinaryStream или getAsciiStream вместо getBlob или методы getClob большие текстовые или двоичные значения в виде потоков. Начиная с версии 1.2, [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) класс предоставляет новый get\<типа > потока методы для этой цели.  
  
-   Убедитесь, что столбцы со значениями потенциально большого объема размещаются последними в списке столбцов в инструкции SELECT и что get\<типа > потока методы [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) используются для доступа к столбцам порядке, в котором они были выбраны.  
  
-   Убедитесь, что параметры OUT со значениями потенциально большого объема объявляются последними в списке параметров в инструкции SQL, используемый для создания [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md). Кроме того, убедитесь, что get\<типа > потока методы [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) используются для доступа к параметрам OUT в порядке их объявления.  
  
-   Старайтесь не выполнять более одной инструкции относительно одного соединения одновременно. Выполнение другой инструкции до обработки результатов предыдущей инструкции может привести к тому, что необработанные результаты будут загружаться в память приложения.  
  
-   Существуют случаи, где с помощью **selectMethod = cursor** вместо **responseBuffering = адаптивной** может оказаться более эффективным, такие как:  
  
    -   Если приложение обрабатывает только вперед, чтения результирующий набор только для медленно, например, при считывании каждой строки после введения пользователем каких входных данных, с помощью **selectMethod = cursor** вместо **responseBuffering = адаптивной** может уменьшить потребление ресурсов службой [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
    -   Если приложение обрабатывает два или более однопроходный, только для чтения результирующих наборов в то же время, в том же соединении, использование **selectMethod = cursor** вместо **responseBuffering = адаптивной** могут помочь Уменьшите память, необходимую драйверу для обработки этих результирующих наборов.  
  
     В обоих случаях необходимо учитывать чрезмерное потребление ресурсов при создании, считывании и закрытии серверных курсоров.  
  
 Помимо этого, в следующем списке приводятся рекомендации для прокручиваемых и однопроходных обновляемых результирующих наборов.  
  
-   Для прокручиваемых результирующих наборов при возвращении блока строк драйвер всегда считывает в память число строк, указанных методом [getFetchSize](../../connect/jdbc/reference/getfetchsize-method-sqlserverresultset.md) метод [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) объекта, даже если включена Адаптивная буферизация. Если прокрутка вызывает OutOfMemoryError, можно уменьшить число строк, возвращаемых при вызове [setFetchSize](../../connect/jdbc/reference/setfetchsize-method-sqlserverresultset.md) метод [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) объекта, чтобы задать размеру выборки меньшее число строк, даже задать 1, если это необходимо. Если это не помешает OutOfMemoryError, не следует включать столбцы очень большого объема в прокручиваемые результирующие наборы.  
  
-   Для однопроходных обновляемых результирующих наборов при возвращении блока строк драйвер обычно считывает в память число строк, указанных методом [getFetchSize](../../connect/jdbc/reference/getfetchsize-method-sqlserverresultset.md) метод [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) объекта, даже когда Адаптивная буферизация включена для соединения. Если вызов [Далее](../../connect/jdbc/reference/next-method-sqlserverresultset.md) метод [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) приводит объект OutOfMemoryError, можно уменьшить число строк, возвращаемых при вызове [setFetchSize](../../connect/jdbc/reference/setfetchsize-method-sqlserverresultset.md) метод [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) объекта, чтобы задать размеру выборки меньшее число строк, даже задать 1, при необходимости. Можно также запретить драйверу помещать в буфер все строки, вызвав [setResponseBuffering](../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md) метод [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) объект с «**адаптивной**"перед выполнение инструкции. Так как результирующий набор не является прокручиваемым, если приложение обращается к значению столбца большого объема с помощью одного из get\<типа > методы поток, драйвер отбрасывает значение, как только приложение его считывает, так же, как для последовательного доступа только для чтения результирующие наборы.  
  
## <a name="see-also"></a>См. также:  
 [Повышение производительности и надежности с помощью драйвера JDBC](../../connect/jdbc/improving-performance-and-reliability-with-the-jdbc-driver.md)  
  
  

