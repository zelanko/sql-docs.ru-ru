---
title: Кэширование метаданных подготовленной инструкции для JDBC Driver | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ''
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 72ef56833f8f6a6ed4cc66a91dcb7a9e4576c7f5
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2018
ms.locfileid: "52395837"
---
# <a name="prepared-statement-metadata-caching-for-the-jdbc-driver"></a>Кэширование метаданных подготовленной инструкции для JDBC Driver
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

В этой статье рассматривается два изменения, которые реализуются для повышения производительности драйвера.

## <a name="batching-of-unprepare-for-prepared-statements"></a>Пакетная обработка Unprepare для подготовленных инструкций
Так как версия 6.1.6-preview, повышение производительности был реализован сводя к минимуму server круговых путей к SQL Server. Ранее для каждого запроса prepareStatement вызов unprepare было также отправлено. Теперь драйвер пакетной обработки unprepare запросы до порогового значения «Параметр ServerPreparedStatementDiscardThreshold», который имеет значение по умолчанию 10.

> [!NOTE]  
>  Пользователи могут изменять значение по умолчанию с помощью следующего метода: setServerPreparedStatementDiscardThreshold (целочисленное значение)

Еще одно изменение, появившиеся с 6.1.6-preview является то, что до этого, драйвер всегда вызвать sp_prepexec. Теперь во время первого выполнения подготовленной инструкции, драйвер вызывает sp_executesql, а для остальных выполняет sp_prepexec и назначает его дескриптор. Дополнительные сведения можно найти [здесь](https://github.com/Microsoft/mssql-jdbc/wiki/PreparedStatement-metadata-caching).

> [!NOTE]  
>  Пользователи могут изменять поведение по умолчанию с предыдущими версиями, всегда вызывать sp_prepexec, параметр enablePrepareOnFirstPreparedStatementCall для **true** следующим образом: setEnablePrepareOnFirstPreparedStatementCall (логическое значение)

### <a name="list-of-the-new-apis-introduced-with-this-change-for-batching-of-unprepare-for-prepared-statements"></a>Список новых интерфейсов API, появившиеся благодаря этому изменению для пакетной обработки Unprepare для подготовленных инструкций

 **SQLServerConnection**
 
|Новый метод|Описание|  
|-----------|-----------------|  
|int getDiscardedServerPreparedStatementCount()|Возвращает количество текущих ожидающих подготовленной инструкции unprepare действия.|
|void closeUnreferencedPreparedStatementHandles()|Заставляет unprepare запросы для любой необработанных отклоненных подготовленных инструкций для выполнения.|
|Логическое getEnablePrepareOnFirstPreparedStatementCall()|Возвращает поведение для определенного подключения экземпляра. Если значение равно false во время первого выполнения вызывает sp_executesql не Подготовка инструкции, после второго выполнения происходит, он вызывает sp_prepexec и фактически установки дескриптором подготовленной инструкции. После выполнения вызовов sp_execute. Это избавляет от для процедура sp_unprepare для подготовленной инструкции close Если инструкция выполняется только один раз. Значение по умолчанию для этого параметра можно изменить, вызывающий setDefaultEnablePrepareOnFirstPreparedStatementCall().|
|void setEnablePrepareOnFirstPreparedStatementCall(boolean value)|Задает поведение для определенного подключения экземпляра. Если значение равно false во время первого выполнения вызывает sp_executesql не Подготовка инструкции, после второго выполнения происходит, он вызывает sp_prepexec и фактически установки дескриптором подготовленной инструкции. После выполнения вызовов sp_execute. Это избавляет от для процедура sp_unprepare для подготовленной инструкции close Если инструкция выполняется только один раз.|
|int getServerPreparedStatementDiscardThreshold()|Возвращает поведение для определенного подключения экземпляра. Этот параметр определяет, сколько необработанных подготовки инструкции отмены действия (процедура sp_unprepare) для подключения, по истечении которого выполняется вызов для очистки незавершенные обработчики на сервере. Если параметр может быть < = 1, unprepare для подготовленной инструкции close действия выполняются немедленно. Если он имеет значение {@literal >} 1, эти вызовы будут объединены в один пакет во избежание использования вызывающий процедура sp_unprepare слишком часто. Значение по умолчанию для этого параметра можно изменить, вызывающий getDefaultServerPreparedStatementDiscardThreshold().|
|void setServerPreparedStatementDiscardThreshold(int value)|Задает поведение для определенного подключения экземпляра. Этот параметр определяет, сколько необработанных подготовки инструкции отмены действия (процедура sp_unprepare) для подключения, по истечении которого выполняется вызов для очистки незавершенные обработчики на сервере. Если параметр может быть < = 1 unprepare действия выполняются немедленно для подготовленной инструкции close. Если он имеет значение > 1 эти вызовы будут объединены в один пакет во избежание издержки вызове процедура sp_unprepare слишком часто.|

 **SQLServerDataSource**
 
|Новый метод|Описание|  
|-----------|-----------------|  
|void setEnablePrepareOnFirstPreparedStatementCall(boolean enablePrepareOnFirstPreparedStatementCall)|Если эта конфигурация имеет значение false первого выполнения подготовленной инструкции вызывает sp_executesql не Подготовка инструкции, после второго выполнения происходит, он вызывает sp_prepexec и фактически установки дескриптором подготовленной инструкции. После выполнения вызовов sp_execute. Это избавляет от для процедура sp_unprepare для подготовленной инструкции close Если инструкция выполняется только один раз.|
|Логическое getEnablePrepareOnFirstPreparedStatementCall()|Если не Подготовка инструкции, после второго выполнения этой конфигурации возвращает значение false, первого выполнения подготовленной инструкции вызывает sp_executesql, он вызывает sp_prepexec и фактически установки дескриптором подготовленной инструкции. После выполнения вызовов sp_execute. Это избавляет от для процедура sp_unprepare для подготовленной инструкции close Если инструкция выполняется только один раз.|
|void setServerPreparedStatementDiscardThreshold(int serverPreparedStatementDiscardThreshold)|Этот параметр определяет, сколько необработанных подготовки инструкции отмены действия (процедура sp_unprepare) для подключения, по истечении которого выполняется вызов для очистки незавершенные обработчики на сервере. Если параметр может быть < = 1 unprepare действия выполняются немедленно для подготовленной инструкции close. Если он имеет значение {@literal >} 1, эти вызовы будут объединены в один пакет во избежание издержки вызове процедура sp_unprepare слишком часто|
|int getServerPreparedStatementDiscardThreshold()|Этот параметр определяет, сколько необработанных подготовки инструкции отмены действия (процедура sp_unprepare) для подключения, по истечении которого выполняется вызов для очистки незавершенные обработчики на сервере. Если параметр может быть < = 1 unprepare действия выполняются немедленно для подготовленной инструкции close. Если он имеет значение {@literal >} 1, эти вызовы будут объединены в один пакет во избежание издержки вызове процедура sp_unprepare слишком часто.|

## <a name="prepared-statement-metatada-caching"></a>Кэширование подготовленной инструкции метаданные
Начиная с версии 6.3.0-preview Microsoft JDBC driver для SQL Server поддерживает кэширование подготовленной инструкции. До v6.3.0-preview Если один выполняет запрос, который был уже подготовленной и сохраненной в кэше, повторный вызов метода тот же запрос не приведет к его подготовки. Теперь драйвер ищет запроса в кэше и найти дескриптор и выполнить ее с sp_execute.
Подготовленный кэширование метаданных инструкции **отключена** по умолчанию. Чтобы включить ее, вам потребуется вызвать следующий метод для объекта connection.

`setStatementPoolingCacheSize(int value)   //value is the desired cache size (any value bigger than 0)`
`setDisableStatementPooling(boolean value) //false allows the caching to take place`

Например: `connection.setStatementPoolingCacheSize(10)`
`connection.setDisableStatementPooling(false)`

### <a name="list-of-the-new-apis-introduced-with-this-change-for-prepared-statement-metadata-caching"></a>Список новых интерфейсов API, появившиеся благодаря этому изменению для подготовленной инструкции кэширование метаданных

 **SQLServerConnection**
 
|Новый метод|Описание|  
|-----------|-----------------|  
|void setDisableStatementPooling(boolean value)|Задает значение true или false пулы инструкций.|
|Логическое getDisableStatementPooling()|Возвращает значение true, если пулы инструкций отключено.|
|void setStatementPoolingCacheSize(int value)|Указывает размер кэша подготовленных инструкций для этого подключения. Значение меньше 1 означает, что без кэширования.|
|int getStatementPoolingCacheSize()|Возвращает размер кэша подготовленных инструкций для этого подключения. Значение меньше 1 означает, что без кэширования.|
|int getStatementHandleCacheEntryCount()|Возвращает текущее число дескрипторов в составе пула подготовленной инструкции.|
|Логическое isPreparedStatementCachingEnabled()|Отвечает за включение пулы инструкций или не для этого подключения.|

 **SQLServerDataSource**
 
|Новый метод|Описание|  
|-----------|-----------------|  
|void setDisableStatementPooling(boolean disableStatementPooling)|Задает пулов инструкций, значение true или false|
|Логическое getDisableStatementPooling()|Возвращает значение true, если пулы инструкций отключено.|
|void setStatementPoolingCacheSize(int statementPoolingCacheSize)|Указывает размер кэша подготовленных инструкций для этого подключения. Значение меньше 1 означает, что без кэширования.|
|int getStatementPoolingCacheSize()|Возвращает размер кэша подготовленных инструкций для этого подключения. Значение меньше 1 означает, что без кэширования.|

## <a name="see-also"></a>См. также:  
 [Повышение производительности и надежности с помощью драйвера JDBC](../../connect/jdbc/improving-performance-and-reliability-with-the-jdbc-driver.md)  
  
  
