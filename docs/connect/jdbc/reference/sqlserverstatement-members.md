---
title: Члены SQLServerStatement | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 828cbaa9-ea7a-4986-95c3-5ba0d7d01d83
caps.latest.revision: 28
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 77161ec9693615eb50d4e62fb9cd1f6f185d23fe
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32853029"
---
# <a name="sqlserverstatement-members"></a>Члены SQLServerStatement
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  В следующих таблицах перечислены члены, предоставляемые [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) класса.  
  
## <a name="constructors"></a>Конструкторы  
 Нет.  
  
## <a name="fields"></a>Поля  
 Нет.  
  
## <a name="inherited-fields"></a>Наследуемые поля  
  
|Название|Описание|  
|----------|-----------------|  
|java.sql.Statement|CLOSE_ALL_RESULTS, CLOSE_CURRENT_RESULT, EXECUTE_FAILED, KEEP_CURRENT_RESULT, NO_GENERATED_KEYS, RETURN_GENERATED_KEYS, SUCCESS_NO_INFO|  
  
## <a name="methods"></a>Методы  
  
|Название|Описание|  
|----------|-----------------|  
|[addBatch](../../../connect/jdbc/reference/addbatch-method-sqlserverstatement.md)|Добавляет заданную команду SQL в текущий список команд для данного [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) объекта.|  
|[cancel](../../../connect/jdbc/reference/cancel-method-sqlserverstatement.md)|Отменяет инструкцию SQL, выполняемую в настоящее время в данном [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) объекта.|  
|[clearBatch](../../../connect/jdbc/reference/clearbatch-method-sqlserverstatement.md)|Обнуляет текущий список команд SQL для этого [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) объекта.|  
|[clearWarnings](../../../connect/jdbc/reference/clearwarnings-method-sqlserverstatement.md)|Удаляет все предупреждения, имена которых присутствуют в данном [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) объекта.|  
|[Закрыть](../../../connect/jdbc/reference/close-method-sqlserverstatement.md)|Это освобождает [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) базы данных и ресурсы JDBC вместо ожидания их автоматического освобождения объекта.|  
|[execute](../../../connect/jdbc/reference/execute-method-sqlserverstatement.md)|Выполняет заданную инструкцию SQL, которая может возвращать несколько результатов.|  
|[executeBatch](../../../connect/jdbc/reference/executebatch-method-sqlserverstatement.md)|Отправляет пакет команд базе данных для выполнения. В случае успешного выполнения всех команд возвращает массив из количества операций обновления, выполненных той или иной командой.|  
|[executeQuery](../../../connect/jdbc/reference/executequery-method-sqlserverstatement.md)|Выполняет заданную инструкцию SQL и возвращает один [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта.|  
|[executeUpdate](../../../connect/jdbc/reference/executeupdate-method-sqlserverstatement.md)|Выполняет заданную инструкцию SQL, которой может быть инструкция INSERT, UPDATE, MERGE или DELETE, либо инструкцию SQL, не возвращающую значения, например инструкцию SQL DDL.|  
|[getConnection](../../../connect/jdbc/reference/getconnection-method-sqlserverstatement.md)|Извлекает [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) , создающего это [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) объекта.|  
|[getFetchDirection](../../../connect/jdbc/reference/getfetchdirection-method-sqlserverstatement.md)|Извлекает направление для выборки строк из таблиц базы данных, значение по умолчанию для результирующих наборов, созданных из этого [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) объекта.|  
|[getFetchSize](../../../connect/jdbc/reference/getfetchsize-method-sqlserverstatement.md)|Возвращает число результирующих наборов строк, является размер выборки по умолчанию для результирующего набора объектов, созданных из этого [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) объекта.|  
|[getGeneratedKeys](../../../connect/jdbc/reference/getgeneratedkeys-method-sqlserverstatement.md)|Извлекает все автоматически сформированные ключи, созданные в результате при выполнении этого [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) объекта.|  
|[getMaxFieldSize](../../../connect/jdbc/reference/getmaxfieldsize-method-sqlserverstatement.md)|Возвращает максимальное число байтов, которые могут возвращаться для значений символьных и двоичных столбцов в [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта, созданного этим [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) объекта.|  
|[getMaxRows](../../../connect/jdbc/reference/getmaxrows-method-sqlserverstatement.md)|Возвращает максимальное число строк, [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта, созданного этим [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) может содержаться в объекте.|  
|[getMoreResults](../../../connect/jdbc/reference/getmoreresults-method-sqlserverstatement.md)|Переходит к следующему результату [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) объекта.|  
|[getQueryTimeout](../../../connect/jdbc/reference/getquerytimeout-method-sqlserverstatement.md)|Извлекает количество секунд [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] будет ожидать это [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) выполнения объекта.|  
|[getResponseBuffering](../../../connect/jdbc/reference/getresponsebuffering-method-sqlserverstatement.md)|Извлекает режим буферизации для этого ответов [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) объекта.|  
|[getResultSet](../../../connect/jdbc/reference/getresultset-method-sqlserverstatement.md)|Извлекает текущий результат в виде [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта.|  
|[getResultSetConcurrency](../../../connect/jdbc/reference/getresultsetconcurrency-method-sqlserverstatement.md)|Получает результирующий набор с параллелизмом для [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекты, созданные этим [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) объекта.|  
|[getResultSetHoldability](../../../connect/jdbc/reference/getresultsetholdability-method-sqlserverstatement.md)|Получает результирующий набор удержания для [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекты, созданные этим [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) объекта.|  
|[getResultSetType](../../../connect/jdbc/reference/getresultsettype-method-sqlserverstatement.md)|Получает тип для результирующего набора [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекты, созданные этим [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) объекта.|  
|[getUpdateCount](../../../connect/jdbc/reference/getupdatecount-method-sqlserverstatement.md)|Возвращает текущий результат в виде счетчика обновлений.|  
|[getWarnings](../../../connect/jdbc/reference/getwarnings-method-sqlserverstatement.md)|Возвращает первое предупреждение, полученных от вызовов в этом [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) объекта.|  
|[IsClosed](../../../connect/jdbc/reference/isclosed-method-sqlserverstatement.md)|Указывает, является ли это [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) объект был закрыт.|  
|[isPoolable](../../../connect/jdbc/reference/ispoolable-method-sqlserverstatement.md)|Возвращает значение, показывающее, можно ли добавить инструкцию в предоставляемый пользователем пул инструкций.|  
|[isWrapperFor](../../../connect/jdbc/reference/iswrapperfor-method-sqlserverstatement.md)|Указывает, является ли этот объект инструкции оболочкой указанного интерфейса.|  
|[setCursorName](../../../connect/jdbc/reference/setcursorname-method-sqlserverstatement.md)|Присваивает имени курсора SQL значение заданной строки. Это значение будет использоваться при дальнейших вызовах метода execute.|  
|[setEscapeProcessing](../../../connect/jdbc/reference/setescapeprocessing-method-sqlserverstatement.md)|Задается режим обработки escape-последовательностей.|  
|[setFetchDirection](../../../connect/jdbc/reference/setfetchdirection-method-sqlserverstatement.md)|Определяет указание для драйвера JDBC относительно направления, в котором будут обрабатываться строки результирующего набора.|  
|[setFetchSize](../../../connect/jdbc/reference/setfetchsize-method-sqlserverstatement.md)|Определяет указание для драйвера JDBC относительно числа строк, которые должны быть извлечены из базы данных при необходимости в дополнительных строках.|  
|[setMaxFieldSize](../../../connect/jdbc/reference/setmaxfieldsize-method-sqlserverstatement.md)|Задает ограничение на максимальное число байтов в [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) столбца хранятся символьные или двоичные значения заданного числа байтов.|  
|[setMaxRows](../../../connect/jdbc/reference/setmaxrows-method-sqlserverstatement.md)|Задает ограничение на максимальное число строк, чтобы любое [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объектов могут содержать до указанного числа.|  
|[setPoolable](../../../connect/jdbc/reference/setpoolable-method-sqlserverstatement.md)|Запрашивает поддержку пулов или запрет пулов в инструкции.|  
|[setQueryTimeout](../../../connect/jdbc/reference/setquerytimeout-method-sqlserverstatement.md)|Задает количество секунд, драйвер будет ожидать [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) указанное число секунд выполнения объекта.|  
|[setResponseBuffering](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md)|Задает режим буферизации для этого ответов [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) объекта без учета регистра **полная строка** или **адаптивной**.|  
|[Извлечение из оболочки](../../../connect/jdbc/reference/unwrap-method-sqlserverstatement.md)|Возвращает объект, реализующий указанный интерфейс для доступа к [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]-определенных методов.|  
  
## <a name="inherited-methods"></a>Наследуемые методы  
  
|Класс, из которого наследуется:|Методы|  
|---------------------------|-------------|  
|java.lang.Object|clone, equals, getClass, hashCode, notify, notifyAll, toString, wait|  
|java.sql.Wrapper|isWrapperFor, unwrap|  
  
## <a name="see-also"></a>См. также  
 [Класс SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
