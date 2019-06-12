---
title: Использование адаптивной буферизации | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 92d4e3be-c3e9-4732-9a60-b57f4d0f7cb7
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 160300be692ff21af1cc33c1fd6fc49d415b22e5
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66790314"
---
# <a name="using-adaptive-buffering"></a>Использование адаптивной буферизации

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Адаптивная буферизация, разработана для получения любых данных большого объема без затрат на использование серверных курсоров. Приложения могут использовать функцию адаптивной буферизации со всеми версиями [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], поддерживаемыми драйвером.

Как правило, когда драйвер [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] выполняет запрос, он получает все результаты с сервера и загружает их в память приложения. Хотя при таком подходе минимизируется потребление ресурсов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], в приложении JDBC может возникнуть ошибка OutOfMemoryError для запросов, возвращающих слишком большие результаты.

Чтобы приложения могли обрабатывать результаты очень большого объема, драйвер [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] реализует адаптивную буферизацию. При адаптивной буферизации драйвер извлекает результаты выполнения инструкции из экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] по мере того, как они нужны приложению, а не все сразу. Драйвер также удаляет результаты, когда приложение теряет к ним доступ. Ниже приводятся примеры ситуаций, когда адаптивная буферизация может быть полезной.

- **Запрос возвращает результирующий набор очень большого объема**. Приложение может выполнить инструкцию SELECT, возвращающую больше строк, чем может уместиться в памяти приложения. В предыдущих версиях приложение должно было использовать серверный курсор, чтобы избежать ошибки OutOfMemoryError. Адаптивная буферизация обеспечивает возможность однопроходного просмотра данных в режиме только для чтения для результирующего набора произвольно большого объема без использования курсора сервера.

- **В результате запроса создаются очень большие столбцы** [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) **или значения параметров OUT** [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) **.** Приложение может получить одно значение (столбец или параметр OUT), которое слишком велико, чтобы целиком поместиться в память приложения. Адаптивная буферизация позволяет клиентскому приложению извлекать такое значение в виде потока, с помощью getAsciiStream, getBinaryStream или методы getCharacterStream. Приложение извлекает значение из экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] по мере чтения потока.

> [!NOTE]  
> Благодаря адаптивной буферизации драйвер JDBC помещает в буфер только необходимое количество данных. Драйвер не позволяет любому открытому методу контролировать или ограничивать размер буфера.

## <a name="setting-adaptive-buffering"></a>Настройка адаптивной буферизации

Начиная с драйвера JDBC версии 2.0 по умолчанию используется значение **adaptive**. Другими словами, чтобы получить адаптивное поведение буферизации, приложению не нужно запрашивать адаптивное поведение явным образом. Но в версии 1.2 по умолчанию использовался режим **полной** буферизации, поэтому приложение должно было запросить режим адаптивной буферизации явным образом.

Существуют три способа, с помощью которых приложение может запросить выполнение адаптивной буферизации.

- Приложение может задать свойство соединения **responseBuffering** значение «adaptive». Дополнительные сведения о настройке свойств соединения, см. в разделе [заданию свойств соединения](../../connect/jdbc/setting-the-connection-properties.md).

- Приложение может использовать метод [setResponseBuffering](../../connect/jdbc/reference/setresponsebuffering-method-sqlserverdatasource.md) объекта [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md) для установки режима буферизации ответов для всех подключений, созданных посредством объекта [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md).

- Приложение может использовать метод [setResponseBuffering](../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md) класса [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md), чтобы установить режим буферизации ответов для определенного объекта инструкции.

При использовании драйвера JDBC версии 1.2 приложения должны были приводить объект инструкции к классу [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md), чтобы использовать метод [setResponseBuffering](../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md). В примерах кода в [большой образец данных чтения](../../connect/jdbc/reading-large-data-sample.md) и [чтение больших данных с помощью хранимой процедуры примера](../../connect/jdbc/reading-large-data-with-stored-procedures-sample.md) показана эта устаревшая практика.

Однако начиная с драйвера JDBC версии 2.0 приложения могут использовать методы [isWrapperFor](../../connect/jdbc/reference/iswrapperfor-method-sqlserverstatement.md) и [unwrap](../../connect/jdbc/reference/unwrap-method-sqlserverstatement.md) для получения доступа к функциям, предоставляемым поставщиками, без необходимости реализации иерархии класса. Пример кода, см. в разделе [обновление большой образец данных](../../connect/jdbc/updating-large-data-sample.md) раздела.

## <a name="retrieving-large-data-with-adaptive-buffering"></a>Извлечение данных большого объема при помощи адаптивной буферизации

Когда большие значения считываются в первый раз с помощью методов get\<Type>Stream и выполняется доступ к столбцам ResultSet и параметрам OUT CallableStatement в порядке возвращения из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], адаптивная буферизация минимизирует использование памяти приложения при обработке результатов. При использовании адаптивной буферизации происходит следующее.

- Методы get\<Type>Stream, определенные в классах [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) и [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md), возвращают потоки только для чтения по умолчанию, хотя потоки можно сбросить, если они выделены приложением. Если приложению необходимо выполнить операцию `reset` для сброса потока, оно сначала должно вызвать метод `mark` для этого потока.

- Методы get\<Type>Stream, определенные в классах [SQLServerClob](../../connect/jdbc/reference/sqlserverclob-class.md) и [SQLServerBlob](../../connect/jdbc/reference/sqlserverblob-class.md), возвращают потоки, которые всегда можно переместить в начальное положение потока без вызова метода `mark`.

Когда приложение использует адаптивную буферизацию, значения, извлекаемые методами get\<Type>Stream, могут быть извлечены только один раз. Если выполняется попытка вызвать какой-либо метод get\<Type> для того же столбца или параметра после вызова метода get\<Type>Stream того же объекта, возникает исключение с сообщением: "Доступ к данным уже был осуществлен, данные недоступны для этого столбца или параметра".

> [!NOTE]
> Вызов ResultSet.close() процессе обработки результирующий набор, потребуется Microsoft JDBC Driver для SQL Server для чтения и отменить все оставшиеся пакеты. Если запрос возвращает большой набор данных, и особенно в том случае, если сетевое подключение работает медленно, это может занять значительное время.

## <a name="guidelines-for-using-adaptive-buffering"></a>Руководство по использованию адаптивной буферизации

Разработчики должны следовать данному руководству для минимизации использования памяти приложением.

- Старайтесь не использовать свойство строки подключения **selectMethod=cursor**, позволяющее приложению обрабатывать результирующий набор очень большого объема. Функция адаптивной буферизации позволяет приложениям обрабатывать очень большие однопроходные результирующие наборы, доступные только для чтения, без использования серверного курсора. Обратите внимание, что задание параметра **selectMethod=cursor** оказывает влияние на все однопроходные результирующие наборы только для чтения, формируемые этим подключением. Другими словами, если приложение рутинно обрабатывает короткие результирующие наборы с несколькими строками, создание, считывание и закрытие серверного курсора для каждого результирующего набора будет использовать больше ресурсов как на стороне клиента, так и на стороне сервера, чем в случае, когда параметру **selectMethod** не присвоено значение **cursor**.

- Считывайте большие текстовые или двоичные значения в виде потока с помощью getAsciiStream, getBinaryStream или методы getCharacterStream вместо getBlob или getClob методы. Начиная с версии 1.2 класс [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) предоставляет новые методы get\<Type>Stream для этой цели.

- Убедитесь в том, что столбцы со значениями потенциально большого объема размещаются последними в списке столбцов в инструкции SELECT и что методы get\<Type>Stream класса [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) используются для доступа к столбцам в порядке их выбора.

- Убедитесь в том, что параметры OUT со значениями потенциально большого объема объявляются последними в списке параметров в инструкции SQL, используемой для создания [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md). Кроме того, убедитесь в том, что методы get\<Type>Stream класса [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) используются для доступа к параметрам OUT в порядке их объявления.

- Старайтесь не выполнять более одной инструкции относительно одного соединения одновременно. Выполнение другой инструкции до обработки результатов предыдущей инструкции может привести к тому, что необработанные результаты будут загружаться в память приложения.

- Существуют случаи, когда использование **selectMethod = cursor** вместо **responseBuffering = адаптивной** может оказаться более эффективным, такие как:

  - Если приложение обрабатывает однопроходной, чтения результирующий набор только для медленно, например, при считывании каждой строки после введения пользователем, с помощью **selectMethod = cursor** вместо **responseBuffering = адаптивной** может уменьшить потребление ресурсов службой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

  - Если приложение обрабатывает два или более однопроходных результирующих набора только для чтения одновременно относительно одного подключения, использование **selectMethod=cursor** вместо **responseBuffering=adaptive** может уменьшить память, необходимую драйверу для обработки этих результирующих наборов.

  В обоих случаях необходимо учитывать чрезмерное потребление ресурсов при создании, считывании и закрытии серверных курсоров.

Помимо этого, в следующем списке приводятся рекомендации для прокручиваемых и однопроходных обновляемых результирующих наборов.

- Для прокручиваемых результирующих наборов при возвращении блока строк драйвер всегда считывает число строк, указанных методом [getFetchSize](../../connect/jdbc/reference/getfetchsize-method-sqlserverresultset.md) объекта [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md), даже если включена адаптивная буферизация. Если прокручивание вызывает ошибку OutOfMemoryError, можно уменьшить число строк, возвращаемых при вызове метода [setFetchSize](../../connect/jdbc/reference/setfetchsize-method-sqlserverresultset.md) объекта [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md), чтобы задать в качестве размера выборки меньшее число строк. При необходимости можно даже задать 1 строку. Если это не позволяет устранить ошибку OutOfMemoryError, старайтесь не включать столбцы очень большого объема в прокручиваемые результирующие наборы.

- Для однопроходных обновляемых результирующих наборов при возвращении блока строк драйвер обычно считывает в память число строк, указанное методом [getFetchSize](../../connect/jdbc/reference/getfetchsize-method-sqlserverresultset.md) объекта [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md), даже если для подключения включена адаптивная буферизация. Если вызов метода [next](../../connect/jdbc/reference/next-method-sqlserverresultset.md) объекта [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) приводит к ошибке OutOfMemoryError, можно уменьшить число возвращаемых строк, вызвав метод [setFetchSize](../../connect/jdbc/reference/setfetchsize-method-sqlserverresultset.md) объекта [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md), чтобы задать в качестве размера выборки меньшее число строк. При необходимости можно даже задать 1 строку. Можно также запретить драйверу помещать в буфер строки, вызвав метод [setResponseBuffering](../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md) объекта [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) с параметром "**adaptive**", прежде чем выполнять инструкцию. Так как результирующий набор не является прокручиваемым, если приложение получает доступ к значению столбца большого объема при помощи одного из методов get\<Type>Stream, драйвер отбрасывает значение, как только приложение его считывает, так же как это происходит в случае с однопроходными результирующими наборами только для чтения.

## <a name="see-also"></a>См. также:

[Повышение производительности и надежности с помощью драйвера JDBC](../../connect/jdbc/improving-performance-and-reliability-with-the-jdbc-driver.md)
