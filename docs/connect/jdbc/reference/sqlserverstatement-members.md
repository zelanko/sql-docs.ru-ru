---
title: Элементы SQLServerStatement | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 828cbaa9-ea7a-4986-95c3-5ba0d7d01d83
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 72eededd01cd61d6845cc92bbdfbfd073668dd76
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "67970351"
---
# <a name="sqlserverstatement-members"></a>Члены SQLServerStatement
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  В следующих таблицах перечислены члены, предоставляемые классом [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).  
  
## <a name="constructors"></a>Конструкторы  
 Нет.  
  
## <a name="fields"></a>Поля  
 Нет.  
  
## <a name="inherited-fields"></a>Наследуемые поля  
  
|Имя|Описание|  
|----------|-----------------|  
|java.sql.Statement|CLOSE_ALL_RESULTS, CLOSE_CURRENT_RESULT, EXECUTE_FAILED, KEEP_CURRENT_RESULT, NO_GENERATED_KEYS, RETURN_GENERATED_KEYS, SUCCESS_NO_INFO|  
  
## <a name="methods"></a>Методы  
  
|Имя|Описание|  
|----------|-----------------|  
|[addBatch](../../../connect/jdbc/reference/addbatch-method-sqlserverstatement.md)|Добавляет заданную команду SQL в текущий список команд для этого объекта [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).|  
|[cancel](../../../connect/jdbc/reference/cancel-method-sqlserverstatement.md)|Отменяет инструкцию SQL, выполняемую в настоящее время объектом [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).|  
|[clearBatch](../../../connect/jdbc/reference/clearbatch-method-sqlserverstatement.md)|Обнуляет текущий список команд SQL для данного объекта [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).|  
|[clearWarnings](../../../connect/jdbc/reference/clearwarnings-method-sqlserverstatement.md)|Очищает все предупреждения, выданные для данного объекта [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).|  
|[close](../../../connect/jdbc/reference/close-method-sqlserverstatement.md)|Немедленно освобождает базу данных и ресурсы JDBC данного объекта [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md), не дожидаясь их автоматического освобождения.|  
|[execute](../../../connect/jdbc/reference/execute-method-sqlserverstatement.md)|Выполняет заданную инструкцию SQL, которая может возвращать несколько результатов.|  
|[executeBatch](../../../connect/jdbc/reference/executebatch-method-sqlserverstatement.md)|Отправляет пакет команд базе данных для выполнения. В случае успешного выполнения всех команд возвращает массив из количества операций обновления, выполненных той или иной командой.|  
|[executeQuery](../../../connect/jdbc/reference/executequery-method-sqlserverstatement.md)|Выполняет заданную инструкцию SQL и возвращает один объект [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).|  
|[executeUpdate](../../../connect/jdbc/reference/executeupdate-method-sqlserverstatement.md)|Выполняет заданную инструкцию SQL, которой может быть инструкция INSERT, UPDATE, MERGE или DELETE, либо инструкцию SQL, не возвращающую значения, например инструкцию SQL DDL.|  
|[getConnection](../../../connect/jdbc/reference/getconnection-method-sqlserverstatement.md)|Возвращает объект [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md), создавший данный объект [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).|  
|[getFetchDirection](../../../connect/jdbc/reference/getfetchdirection-method-sqlserverstatement.md)|Извлекает направление выборки строк из таблиц базы данных, заданное по умолчанию для результирующих наборов, созданных на основе этого объекта [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).|  
|[getFetchSize](../../../connect/jdbc/reference/getfetchsize-method-sqlserverstatement.md)|Извлекает число строк результирующего набора, равное размеру выборки по умолчанию для объектов результирующих наборов, созданных на основе этого объекта [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).|  
|[getGeneratedKeys](../../../connect/jdbc/reference/getgeneratedkeys-method-sqlserverstatement.md)|Извлекает все автоматически сформированные ключи, созданные в результате выполнения этого объекта [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).|  
|[getMaxFieldSize](../../../connect/jdbc/reference/getmaxfieldsize-method-sqlserverstatement.md)|Извлекает максимальный размер (в байтах) для возвращаемых значений символьных и двоичных столбцов в объекте [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md), созданном объектом [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).|  
|[getMaxRows](../../../connect/jdbc/reference/getmaxrows-method-sqlserverstatement.md)|Извлекает максимальное количество строк, которое может содержаться в объекте [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md), созданном объектом [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).|  
|[getMoreResults](../../../connect/jdbc/reference/getmoreresults-method-sqlserverstatement.md)|Переходит к следующему результату этого объекта [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).|  
|[getQueryTimeout](../../../connect/jdbc/reference/getquerytimeout-method-sqlserverstatement.md)|Извлекает время в секундах, в течение которого [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] будет ожидать выполнения этого объекта [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).|  
|[getResponseBuffering](../../../connect/jdbc/reference/getresponsebuffering-method-sqlserverstatement.md)|Извлекает режим буферизации ответов для этого объекта [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).|  
|[getResultSet](../../../connect/jdbc/reference/getresultset-method-sqlserverstatement.md)|Извлекает текущий результат как объект [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).|  
|[getResultSetConcurrency](../../../connect/jdbc/reference/getresultsetconcurrency-method-sqlserverstatement.md)|Возвращает параллелизм результирующего набора для объектов [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md), созданных этим объектом [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).|  
|[getResultSetHoldability](../../../connect/jdbc/reference/getresultsetholdability-method-sqlserverstatement.md)|Возвращает возможность сохранения результирующих наборов для объектов [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md), созданных этим объектом [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).|  
|[getResultSetType](../../../connect/jdbc/reference/getresultsettype-method-sqlserverstatement.md)|Возвращает тип результирующего набора для объектов [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md), созданных этим объектом [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).|  
|[getUpdateCount](../../../connect/jdbc/reference/getupdatecount-method-sqlserverstatement.md)|Возвращает текущий результат в виде счетчика обновлений.|  
|[getWarnings](../../../connect/jdbc/reference/getwarnings-method-sqlserverstatement.md)|Возвращает первое предупреждение, указанное в отчетах для вызовов этого объекта [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).|  
|[isClosed](../../../connect/jdbc/reference/isclosed-method-sqlserverstatement.md)|Указывает, был ли закрыт этот объект [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).|  
|[isPoolable](../../../connect/jdbc/reference/ispoolable-method-sqlserverstatement.md)|Возвращает значение, показывающее, можно ли добавить инструкцию в предоставляемый пользователем пул инструкций.|  
|[isWrapperFor](../../../connect/jdbc/reference/iswrapperfor-method-sqlserverstatement.md)|Указывает, является ли этот объект инструкции оболочкой указанного интерфейса.|  
|[setCursorName](../../../connect/jdbc/reference/setcursorname-method-sqlserverstatement.md)|Присваивает имени курсора SQL значение заданной строки. Это значение будет использоваться при дальнейших вызовах метода execute.|  
|[setEscapeProcessing](../../../connect/jdbc/reference/setescapeprocessing-method-sqlserverstatement.md)|Задается режим обработки escape-последовательностей.|  
|[setFetchDirection](../../../connect/jdbc/reference/setfetchdirection-method-sqlserverstatement.md)|Определяет указание для драйвера JDBC относительно направления, в котором будут обрабатываться строки результирующего набора.|  
|[setFetchSize](../../../connect/jdbc/reference/setfetchsize-method-sqlserverstatement.md)|Определяет указание для драйвера JDBC относительно числа строк, которые должны быть извлечены из базы данных при необходимости в дополнительных строках.|  
|[setMaxFieldSize](../../../connect/jdbc/reference/setmaxfieldsize-method-sqlserverstatement.md)|Устанавливает ограничение количества байтов для максимального размера столбца [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md), в котором хранятся символьные или двоичные значения.|  
|[setMaxRows](../../../connect/jdbc/reference/setmaxrows-method-sqlserverstatement.md)|Устанавливает равное заданному числу ограничение для максимального количества строк, которое может содержаться в объекте [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).|  
|[setPoolable](../../../connect/jdbc/reference/setpoolable-method-sqlserverstatement.md)|Запрашивает поддержку пулов или запрет пулов в инструкции.|  
|[setQueryTimeout](../../../connect/jdbc/reference/setquerytimeout-method-sqlserverstatement.md)|Задает время в секундах, в течение которого драйвер будет ожидать выполнения объекта [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).|  
|[setResponseBuffering](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md)|Задает режиму буферизации ответов для этого объекта [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) значение **String full** или **adaptive** без учета регистра.|  
|[unwrap](../../../connect/jdbc/reference/unwrap-method-sqlserverstatement.md)|Возвращает объект, реализующий указанный интерфейс для доступа к методам, относящимся к драйверу [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)].|  
  
## <a name="inherited-methods"></a>Наследуемые методы  
  
|Класс, из которого наследуется:|Методы|  
|---------------------------|-------------|  
|java.lang.Object|clone, equals, getClass, hashCode, notify, notifyAll, toString, wait|  
|java.sql.Wrapper|isWrapperFor, unwrap|  
  
## <a name="see-also"></a>См. также:  
 [Класс SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
