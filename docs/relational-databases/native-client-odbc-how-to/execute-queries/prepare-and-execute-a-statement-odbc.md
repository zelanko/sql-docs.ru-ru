---
title: Подготовьте и выполнить заявление (ODBC) Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- statement execution
- statement preparation
ms.assetid: 0adecc63-4da5-486c-bc48-09a004a2fae6
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: eaf7e3518f369639ba3d2eb854a103ff839276c7
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81294163"
---
# <a name="prepare-and-execute-a-statement-odbc"></a>Подготовка и выполнение инструкцию (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

    
### <a name="to-prepare-a-statement-once-and-then-execute-it-multiple-times"></a>Однократная подготовка инструкции и многократное ее выполнение  
  
1.  Вызовите функцию [SQLPrepare](https://go.microsoft.com/fwlink/?LinkId=59360) , чтобы подготовить инструкцию.  
  
2.  Можно также вызвать метод [SQLNumParams](https://go.microsoft.com/fwlink/?LinkId=58404) , чтобы определить количество параметров в подготовленной инструкции.  
  
3.  Выполните следующие действия для каждого параметра подготовленной инструкции (не обязательно).  
  
    -   Вызовите [SQLDescribeParam](../../../relational-databases/native-client-odbc-api/sqldescribeparam.md) для получения сведений о параметре.  
  
    -   Привяжите каждый параметр к переменной программы с помощью [SQLBindParameter](../../../relational-databases/native-client-odbc-api/sqlbindparameter.md). Присвойте значения всем параметрам времени выполнения.  
  
4.  Перед каждым выполнением подготовленной инструкции.  
  
    -   Если в инструкции имеются маркеры параметров, поместите значения данных в буфер связанного параметра.  
  
    -   Вызовите функцию [SQLExecute](https://go.microsoft.com/fwlink/?LinkId=58400) , чтобы выполнить подготовленную инструкцию.  
  
    -   При использовании входных параметров времени выполнения функция [SQLExecute](https://go.microsoft.com/fwlink/?LinkId=58400) возвращает SQL_NEED_DATA. Отправьте данные по фрагментам при помощи функций [SQLParamData](https://go.microsoft.com/fwlink/?LinkId=58405) и [SQLPutData](../../../relational-databases/native-client-odbc-api/sqlputdata.md).  
  
### <a name="to-prepare-a-statement-with-column-wise-parameter-binding"></a>Подготовка инструкции с привязкой параметра на уровне столбца  
  
1.  Вызовите функцию [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) , чтобы задать следующие атрибуты.  
  
    -   Атрибуту SQL_ATTR_PARAMSET_SIZE задайте число наборов параметров (S).  
  
    -   Атрибуту SQL_ATTR_PARAM_BIND_TYPE задайте значение SQL_PARAMETER_BIND_BY_COLUMN.  
  
    -   Атрибут SQL_ATTR_PARAMS_PROCESSED_PTR должен указывать на переменную SQLUINTEGER, в которую помещается число обработанных параметров.  
  
    -   Задайте значение SQL_ATTR_PARAMS_STATUS_PTR, которое указывает на массив [S] переменных SQLUSSMALLINT, предназначенный для сохранения признаков состояния параметра.  
  
2.  Подвлавайте s'LPrepare для подготовки заявления.  
  
3.  Можно также вызвать метод [SQLNumParams](https://go.microsoft.com/fwlink/?LinkId=58404) , чтобы определить количество параметров в подготовленной инструкции.  
  
4.  По желанию, для каждого параметра в подготовленном заявлении позвоните по телефону S'LDescribeParam, чтобы получить информацию о параметрах.  
  
5.  Для каждого маркера параметра выполните следующее.  
  
    -   Выделите массив из S буферов параметра для сохранения значений данных.  
  
    -   Выделите массив из S буферов параметра для сохранения длин данных.  
  
    -   Вызовите функцию SQLBindParameter , чтобы связать массивы значений данных и длин данных с параметром инструкции.  
  
    -   Если параметр использует данные времени выполнения типов text или image, присвойте ему значение.  
  
    -   Если используются параметры с данными времени выполнения, присвойте им значения.  
  
6.  Перед каждым выполнением подготовленной инструкции.  
  
    -   Поместите значения и длины S-данных в массивы связанных параметров.  
  
    -   Вызовите функцию SQLExecute, чтобы выполнить подготовленную инструкцию.  
  
    -   При использовании входных параметров времени выполнения функция SQLExecute возвращает SQL_NEED_DATA. Отправьте данные по фрагментам при помощи функций SQLParamData и SQLPutData.  
  
### <a name="to-prepare-a-statement-with-row-wise-bound-parameters"></a>Подготовка инструкции с привязкой параметра на уровне строки  
  
1.  Выделите массив структур [S], где S — число наборов параметров. Структура имеет по одному элементу для каждого параметра, а каждый элемент состоит из двух частей.  
  
    -   Первая часть — переменная соответствующего типа данных, в которую помещаются данные параметра.  
  
    -   Вторая часть — переменная SQLINTEGER, в которую помещается признак состояния.  
  
2.  Вызовите функцию [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) , чтобы задать следующие атрибуты.  
  
    -   Атрибуту SQL_ATTR_PARAMSET_SIZE задайте число наборов параметров (S).  
  
    -   Атрибуту SQL_ATTR_PARAM_BIND_TYPE задайте размер структуры, выделенной в шаге 1.  
  
    -   Атрибут SQL_ATTR_PARAMS_PROCESSED_PTR должен указывать на переменную SQLUINTEGER, в которую помещается число обработанных параметров.  
  
    -   Задайте значение SQL_ATTR_PARAMS_STATUS_PTR, которое указывает на массив [S] переменных SQLUSSMALLINT, предназначенный для сохранения признаков состояния параметра.  
  
3.  Подвлавайте s'LPrepare для подготовки заявления.  
  
4.  Для каждого параметра позвоните по вызову S'LBindParameter, чтобы указать значение данных параметра и указатель длины данных на свои переменные в первом элементе массива структур, выделенных в шаге 1. Если параметр использует данные времени выполнения, присвойте ему значение.  
  
5.  Перед каждым выполнением подготовленной инструкции.  
  
    -   Заполните массив буфера привязанного параметра значениями данных.  
  
    -   Вызовите функцию SQLExecute, чтобы выполнить подготовленную инструкцию. Драйвер эффективно выполнит инструкцию SQL S раз, по одному разу для каждого набора параметров.  
  
    -   При использовании входных параметров времени выполнения функция SQLExecute возвращает SQL_NEED_DATA. Отправьте данные по фрагментам при помощи функций SQLParamData и SQLPutData.  
  
## <a name="see-also"></a>См. также:  
 [Выполнение запросов Как-к темам &#40;ODBC&#41;](../../../relational-databases/native-client-odbc-how-to/execute-queries/executing-queries-how-to-topics-odbc.md)  
  
  
