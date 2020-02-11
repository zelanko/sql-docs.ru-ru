---
title: Функция СклсетконнектаттрфордбЦинфо | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetConnectAttrForDbcInfo function [ODBC]
ms.assetid: a28fadb9-b998-472a-b252-709507e92005
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f16cac6a715716dcef0a1c2b337716835c14b2b7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67910371"
---
# <a name="sqlsetconnectattrfordbcinfo-function"></a>Функция SQLSetConnectAttrForDbcInfo
**Соответствия**  
 Представленная версия: соответствие стандартам ODBC 3,81: ODBC  
  
 **Сводка**  
 **СклсетконнектаттрфордбЦинфо** совпадает с **SQLSetConnectAttr**, но он задает атрибут для маркера сведений о соединении, а не для маркера подключения.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
  
SQLRETURN  SQLSetConnectAttrForDbcInfo(  
                SQLHDBC_INFO_TOKEN    hDbcInfoToken,  
                SQLINTEGER            Attribute,  
                SQLPOINTER            ValuePtr,  
                SQLINTEGER            StringLength );  
```  
  
## <a name="arguments"></a>Аргументы  
 *хдбЦинфотокен*  
 Входной Маркер маркера.  
  
 *attribute*  
 Входной Заданный атрибут. Список допустимых атрибутов зависит от драйвера и соответствует параметру для [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md).  
  
 *ValuePtr*  
 Входной Указатель на значение, которое должно быть связано с *атрибутом*. В зависимости от значения *атрибута* *ValuePtr* будет иметь значение 32-битовое целое число без знака или будет указывать на строку символов, завершающуюся нулем. Обратите внимание, что если аргумент *атрибута* является зависящим от драйвера значением, значение в *ValuePtr* может быть целым числом со знаком.  
  
 *StringLength*  
 Входной Если *атрибут Attribute* является атрибутом, ОПРЕДЕЛЯЕМым ODBC, а *ValuePtr* указывает на символьную строку или двоичный буфер, этот аргумент должен иметь длину **ValuePtr*. Для символьных строковых данных этот аргумент должен содержать число байтов в строке.  
  
 Если *атрибут Attribute* является атрибутом, ОПРЕДЕЛЯЕМым ODBC, а *ValuePtr* — целым числом, *StringLength* игнорируется.  
  
 Если *атрибут* является атрибутом, определяемым драйвером, приложение указывает природу атрибута для диспетчера драйверов, задавая аргумент *StringLength* . *StringLength* могут иметь следующие значения:  
  
-   Если *ValuePtr* является указателем на символьную строку, *StringLength* — это длина строки или SQL_NTS.  
  
-   Если *ValuePtr* является указателем на двоичный буфер, приложение помещает результат макроса SQL_LEN_BINARY_ATTR (*length*) в *StringLength*. Это помещает отрицательное значение в *StringLength*.  
  
-   Если *ValuePtr* является указателем на значение, отличное от символьной строки или двоичной строки, *StringLength* должно иметь значение SQL_IS_POINTER.  
  
-   Если *ValuePtr* содержит значение фиксированной длины, то *StringLength* либо SQL_IS_INTEGER, либо SQL_IS_UINTEGER, соответственно.  
  
## <a name="returns"></a>Возвращает  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 То же, что и [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md), за исключением того, что диспетчер драйверов будет использовать **параметром handletype** SQL_HANDLE_DBC_INFO_TOKEN и **маркер** *хдбЦинфотокен*.  
  
## <a name="remarks"></a>Remarks  
 **СклсетконнектаттрфордбЦинфо** совпадает с **SQLSetConnectAttr**, но он задает атрибут для маркера сведений о соединении, а не для маркера подключения. Например, если **SQLSetConnectAttr** не распознает атрибут, **склсетконнектаттрфордбЦинфо** должен также возвращать SQL_ERROR для этого атрибута.  
  
 Всякий раз, когда драйвер возвращает SQL_ERROR или SQL_INVALID_HANDLE, драйвер должен игнорировать этот атрибут, чтобы вычислить идентификатор пула. Кроме того, диспетчер драйверов будет получать диагностические сведения от *хдбЦинфотокен*и возвращать SQL_SUCCESS_WITH_INFO приложению в [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) и [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md). Поэтому приложение может получить сведения о том, почему не удается установить некоторые атрибуты.  
  
 Приложения не должны вызывать эту функцию напрямую. Драйвер ODBC, поддерживающий пулы соединений с учетом драйверов, должен реализовывать эту функцию.  
  
 Включите склспи. h для разработки драйвера ODBC.  
  
## <a name="see-also"></a>См. также:  
 [Разработка драйвера ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Организация пулов соединений с учетом драйверов](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [Разработка драйвера ODBC с поддержкой пула подключений](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
