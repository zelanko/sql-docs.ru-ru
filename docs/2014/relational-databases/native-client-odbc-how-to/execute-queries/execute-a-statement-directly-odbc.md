---
title: Непосредственное выполнение инструкции (ODBC) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- statement execution
ms.assetid: b690f9de-66e1-4ee5-ab6a-121346fb5f85
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0597054914dcbce7e7b1fb1475beb29bab7b8a57
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "63200405"
---
# <a name="execute-a-statement-directly-odbc"></a>Непосредственное выполнение инструкции (ODBC)
    
### <a name="to-execute-a-statement-directly-and-one-time-only"></a>Однократное непосредственное выполнение инструкции  
  
1.  Если инструкция содержит маркеры параметров, воспользуйтесь [SQLBindParameter](../../native-client-odbc-api/sqlbindparameter.md) для привязки каждого параметра к программной переменной. Необходимо заполнить программные переменные значениями данных, а затем установить все параметры с данными времени выполнения.  
  
2.  Чтобы выполнить инструкцию, вызовите метод [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) .  
  
3.  При использовании входных параметров с данными времени выполнения вызов [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) возвращает SQL_NEED_DATA. Отправьте данные по фрагментам при помощи функций [SQLParamData](https://go.microsoft.com/fwlink/?LinkId=58405) и [SQLPutData](../../native-client-odbc-api/sqlputdata.md).  
  
### <a name="to-execute-a-statement-multiple-times-by-using-column-wise-parameter-binding"></a>Выполнение инструкции несколько раз при помощи привязки параметра на уровне столбца  
  
1.  Вызовите функцию [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) , чтобы задать следующие атрибуты.  
  
     Атрибуту SQL_ATTR_PARAMSET_SIZE задайте число наборов параметров (S).  
  
     Атрибуту SQL_ATTR_PARAM_BIND_TYPE задайте значение SQL_PARAMETER_BIND_BY_COLUMN.  
  
     Атрибут SQL_ATTR_PARAMS_PROCESSED_PTR должен указывать на переменную SQLUINTEGER, в которую помещается число обработанных параметров.  
  
     Атрибут SQL_ATTR_PARAMS_STATUS_PTR должен указывать на массив [S] переменных SQLUSSMALLINT, в которые помещаются признаки состояния параметров.  
  
2.  Для каждого маркера параметра выполните следующее.  
  
     Выделите массив из S буферов параметра для сохранения значений данных.  
  
     Выделите массив из S буферов параметра для сохранения длин данных.  
  
     Вызовите функцию [SQLBindParameter](../../native-client-odbc-api/sqlbindparameter.md) , чтобы связать массивы значений данных и длин данных с параметром инструкции.  
  
     Настройте текстовые столбцы или столбцы изображений, получающие данные во время выполнения.  
  
     Поместите S значений данных и S длин данных в привязанные массивы параметров.  
  
3.  Чтобы выполнить инструкцию, вызовите метод [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) . Драйвер эффективно выполнит инструкцию S раз, по одному разу для каждого набора параметров.  
  
4.  При использовании входных параметров с данными времени выполнения вызов [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) возвращает SQL_NEED_DATA. Отправьте данные по фрагментам при помощи функций [SQLParamData](https://go.microsoft.com/fwlink/?LinkId=58405) и [SQLPutData](../../native-client-odbc-api/sqlputdata.md).  
  
### <a name="to-execute-a-statement-multiple-times-by-using-row-wise-parameter-binding"></a>Выполнение инструкции несколько раз при помощи привязки параметра на уровне строки  
  
1.  Выделите массив структур [S], где S — число наборов параметров. Структура имеет по одному элементу для каждого параметра, а каждый элемент состоит из двух частей.  
  
     Первая часть — переменная соответствующего типа данных, в которую помещаются данные параметра.  
  
     Вторая часть — переменная SQLINTEGER, в которую помещается признак состояния.  
  
2.  Вызовите функцию [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) , чтобы задать следующие атрибуты.  
  
     Атрибуту SQL_ATTR_PARAMSET_SIZE задайте число наборов параметров (S).  
  
     Атрибуту SQL_ATTR_PARAM_BIND_TYPE задайте размер структуры, выделенной в шаге 1.  
  
     Атрибут SQL_ATTR_PARAMS_PROCESSED_PTR должен указывать на переменную SQLUINTEGER, в которую помещается число обработанных параметров.  
  
     Атрибут SQL_ATTR_PARAMS_STATUS_PTR должен указывать на массив [S] переменных SQLUSSMALLINT, в которые помещаются признаки состояния параметров.  
  
3.  Для каждого маркера параметра вызовите функцию [SQLBindParameter](../../native-client-odbc-api/sqlbindparameter.md) , чтобы связать значение данных параметра и указатель на длину его данных с соответствующими переменными в первом элементе массива структур, выделенных на шаге 1. Если параметр использует данные времени выполнения, присвойте ему значение.  
  
4.  Заполните массив буфера привязанного параметра значениями данных.  
  
5.  Чтобы выполнить инструкцию, вызовите метод [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) . Драйвер эффективно выполнит инструкцию S раз, по одному разу для каждого набора параметров.  
  
6.  При использовании входных параметров с данными времени выполнения вызов [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) возвращает SQL_NEED_DATA. Отправьте данные по фрагментам при помощи функций [SQLParamData](https://go.microsoft.com/fwlink/?LinkId=58405) и [SQLPutData](../../native-client-odbc-api/sqlputdata.md).  
  
 **Примечание** . Привязка на уровне столбца и на уровне строк чаще всего используется в сочетании с [функцией SQLPrepare](https://go.microsoft.com/fwlink/?LinkId=59360) и [SQLExecute](https://go.microsoft.com/fwlink/?LinkId=58400) , чем с [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399).  
  
## <a name="see-also"></a>См. также:  
 [Инструкции по выполнению запросов &#40;ODBC&#41;](executing-queries-how-to-topics-odbc.md)  
  
  
