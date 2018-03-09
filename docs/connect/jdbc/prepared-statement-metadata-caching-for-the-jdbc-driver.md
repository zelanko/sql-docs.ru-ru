---
title: "Подготовить кэширование для драйвера JDBC метаданных инструкции | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2018
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
ms.assetid: 
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 13d4c0766552d9472038ffe7f2ff7fed6d73584d
ms.sourcegitcommit: 9d0467265e052b925547aafaca51e5a5e93b7e38
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/02/2018
---
# <a name="prepared-statement-metadata-caching-for-the-jdbc-driver"></a>Кэширование для драйвера JDBC метаданных подготовленной инструкции
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

В этой статье сведения на два изменения, которые реализуются для повышения производительности драйвера.

## <a name="batching-of-unprepare-for-prepared-statements"></a>Пакетирование аннулирующие для подготовленных инструкций
Так как версия 6.1.6-preview, повышение производительности была реализована через минимизация сервера обходов для SQL Server. Ранее для каждого запроса prepareStatement вызов аннулирующие также отправлено. Теперь драйвер пакетной обработки аннулирующие запросы до пороговое значение «ServerPreparedStatementDiscardThreshold», имеет значение по умолчанию 10.

> [!NOTE]  
>  Пользователи могут изменить значение по умолчанию с помощью следующего метода: setServerPreparedStatementDiscardThreshold (целочисленное значение)

Один дополнительные изменениям, вызываемым из 6.1.6-preview — что до этого драйвера всегда будет вызывать sp_prepexec. Теперь для первого выполнения подготовленной инструкции, драйвер вызывает процедуру sp_executesql и для остальных выполняет sp_prepexec и назначает его дескриптор. Дополнительные сведения можно найти [здесь](https://github.com/Microsoft/mssql-jdbc/wiki/PreparedStatement-metadata-caching).

> [!NOTE]  
>  Пользователи могут изменить поведение по умолчанию в предыдущих версиях всегда вызывать sp_prepexec, параметр enablePrepareOnFirstPreparedStatementCall для **true** следующим образом: setEnablePrepareOnFirstPreparedStatementCall (логическое значение)

### <a name="list-of-the-new-apis-introduced-with-this-change-for-batching-of-unprepare-for-prepared-statements"></a>Список новых интерфейсов API, впервые появилась в это изменение для пакетирование аннулирующие для подготовленных инструкций

 **SQLServerConnection**
 
|Новый метод|Описание|  
|-----------|-----------------|  
|int getDiscardedServerPreparedStatementCount()|Возвращает количество ожидающих подготовленной инструкции аннулирующие действия.|
|void closeUnreferencedPreparedStatementHandles()|Принудительно unprepare запрашивает все невыполненные отклоненных подготовленных инструкций для выполнения.|
|Логическое getEnablePrepareOnFirstPreparedStatementCall()|Возвращает поведение для подключения экземпляра. Если значение равно false во время первого выполнения вызвавшему sp_executesql не Подготовка инструкции, после второго выполнения происходит вызовы sp_prepexec и фактически установки дескриптор подготовленной инструкции. После выполнения вызовов sp_execute. Это избавляет от для sp_unprepare для подготовленной инструкции close, если инструкция выполняется только один раз. Значение по умолчанию для этого параметра можно изменить путем вызова setDefaultEnablePrepareOnFirstPreparedStatementCall().|
|void setEnablePrepareOnFirstPreparedStatementCall(boolean value)|Задает поведение для подключения экземпляра. Если значение равно false во время первого выполнения вызывает sp_executesql не Подготовка инструкции, после второго выполнения происходит вызовы sp_prepexec и фактически установки дескриптор подготовленной инструкции. После выполнения вызовов sp_execute. Это избавляет от для sp_unprepare для подготовленной инструкции close, если инструкция выполняется только один раз.|
|int getServerPreparedStatementDiscardThreshold()|Возвращает поведение для подключения экземпляра. Этот параметр определяет, сколько невыполненных подготовки инструкции отклонения действия (sp_unprepare) обработки для подключения, по истечении которого выполняется вызов для очистки незавершенные обработчики на сервере. Если значение параметра — < = 1, аннулирующие для подготовленной инструкции close действия выполняются немедленно. Если задано значение {@literal >} 1, эти вызовы будут объединены во избежание издержки вызывающий sp_unprepare слишком часто. Значение по умолчанию для этого параметра можно изменить путем вызова getDefaultServerPreparedStatementDiscardThreshold().|
|void setServerPreparedStatementDiscardThreshold(int value)|Задает поведение для подключения экземпляра. Этот параметр определяет, сколько невыполненных подготовки инструкции отклонения действия (sp_unprepare) обработки для подключения, по истечении которого выполняется вызов для очистки незавершенные обработчики на сервере. Если значение параметра — < = 1 аннулирующие действия выполняются немедленно для подготовленной инструкции close. Если значение > 1 эти вызовы группируются вместе, чтобы избежать вызова sp_unprepare слишком часто.|

 **SQLServerDataSource**
 
|Новый метод|Описание|  
|-----------|-----------------|  
|void setEnablePrepareOnFirstPreparedStatementCall(boolean enablePrepareOnFirstPreparedStatementCall)|Если эта конфигурация имеет значение false первого выполнения подготовленной инструкции вызвавшему sp_executesql не Подготовка инструкции, после второго выполнения происходит вызовы sp_prepexec и фактически установки дескриптор подготовленной инструкции. После выполнения вызовов sp_execute. Это избавляет от для sp_unprepare для подготовленной инструкции close, если инструкция выполняется только один раз.|
|Логическое getEnablePrepareOnFirstPreparedStatementCall()|Если эта конфигурация возвращает значение false, первого выполнения подготовленной инструкции вызвавшему sp_executesql и не Подготовка инструкции, после второго выполнения происходит, он вызывает sp_prepexec и фактически установки дескриптор подготовленной инструкции. После выполнения вызовов sp_execute. Это избавляет от для sp_unprepare для подготовленной инструкции close, если инструкция выполняется только один раз.|
|void setServerPreparedStatementDiscardThreshold(int serverPreparedStatementDiscardThreshold)|Этот параметр определяет, сколько невыполненных подготовки инструкции отклонения действия (sp_unprepare) обработки для подключения, по истечении которого выполняется вызов для очистки незавершенные обработчики на сервере. Если значение параметра — < = 1 аннулирующие действия выполняются немедленно для подготовленной инструкции close. Если задано значение {@literal >} объединены этих вызовов, чтобы избежать слишком часто вызова sp_unprepare 1|
|int getServerPreparedStatementDiscardThreshold()|Этот параметр определяет, сколько невыполненных подготовки инструкции отклонения действия (sp_unprepare) обработки для подключения, по истечении которого выполняется вызов для очистки незавершенные обработчики на сервере. Если значение параметра — < = 1 аннулирующие действия выполняются немедленно для подготовленной инструкции close. Если задано значение {@literal >} 1 объединены этих вызовов, чтобы избежать вызова sp_unprepare слишком часто.|

## <a name="prepared-statement-metatada-caching"></a>Подготовленные инструкции метаданные кэширования
Начиная с версии 6.3.0-preview драйвер Microsoft JDBC для SQL Server поддерживает кэширование подготовленной инструкции. До v6.3.0-preview Если один выполняет запрос, который был уже подготовленной и сохраненной в кэше, повторным вызовом тот же запрос не приведет к его подготовки. Теперь драйвер выполняет поиск запроса в кэше и найти дескриптор и выполнить ее с sp_execute.
Кэширование метаданных инструкции подготовленного **отключена** по умолчанию. Чтобы включить его, необходимо вызвать следующий метод в объекте подключения:

`setStatementPoolingCacheSize(int value)   //value is the desired cache size (any value bigger than 0)`
`setDisableStatementPooling(boolean value) //false allows the caching to take place`

Например: `connection.setStatementPoolingCacheSize(10)`
`connection.setDisableStatementPooling(false)`

### <a name="list-of-the-new-apis-introduced-with-this-change-for-prepared-statement-metadata-caching"></a>Список новых интерфейсов API, появившиеся после этого изменения для подготовленной инструкции кэширование метаданных

 **SQLServerConnection**
 
|Новый метод|Описание|  
|-----------|-----------------|  
|void setDisableStatementPooling(boolean value)|Задает значение true или false пулы инструкций.|
|Логическое getDisableStatementPooling()|Возвращает значение true, если инструкция пул недоступен.|
|void setStatementPoolingCacheSize(int value)|Указывает размер кэша подготовленной инструкции для этого подключения. Значение меньше 1 означает без кэширования.|
|int getStatementPoolingCacheSize()|Возвращает размер кэша подготовленной инструкции для этого подключения. Значение меньше 1 означает без кэширования.|
|int getStatementHandleCacheEntryCount()|Возвращает текущее количество дескрипторов пула подготовленной инструкции.|
|Логическое isPreparedStatementCachingEnabled()|Инструкция пул включен или не для этого подключения.|

 **SQLServerDataSource**
 
|Новый метод|Описание|  
|-----------|-----------------|  
|void setDisableStatementPooling(boolean disableStatementPooling)|Задает пулов инструкций значение true или false|
|Логическое getDisableStatementPooling()|Возвращает значение true, если инструкция пул недоступен.|
|void setStatementPoolingCacheSize(int statementPoolingCacheSize)|Указывает размер кэша подготовленной инструкции для этого подключения. Значение меньше 1 означает без кэширования.|
|int getStatementPoolingCacheSize()|Возвращает размер кэша подготовленной инструкции для этого подключения. Значение меньше 1 означает без кэширования.|

## <a name="see-also"></a>См. также  
 [Повышение производительности и надежности с помощью драйвера JDBC](../../connect/jdbc/improving-performance-and-reliability-with-the-jdbc-driver.md)  
  
  
