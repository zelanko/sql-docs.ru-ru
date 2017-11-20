---
title: "Привязка маркеров параметров | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parameter markers [ODBC]
- binding parameter markers [ODBC]
ms.assetid: fe88c1c2-4ee4-45e0-8500-b8c25c047815
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: cd8c39160ee6cafbbc9f041565a57ea29680bef7
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="binding-parameter-markers"></a>Маркеры параметров привязки
Приложение выполняет привязку параметров путем вызова **SQLBindParameter**. **SQLBindParameter** связывает один параметр за раз. С его помощью приложение указывает следующее:  
  
-   Номер параметра. Параметры нумеруются в порядке возрастания параметра в инструкции SQL, начиная с номера 1. Хотя можно задать параметр с номером выше, чем число параметров в инструкции SQL, значение параметра будут игнорироваться при выполнении инструкции.  
  
-   Тип параметра (вход, ввода вывода или выходной). За исключением параметров в вызове процедуры все параметры являются входными параметрами. Дополнительные сведения см. в разделе [параметры процедуры](../../../odbc/reference/develop-app/procedure-parameters.md)далее в этом разделе.  
  
-   C тип, адрес и байтов длина данных переменной, привязанное к параметру. Драйвер должен иметь возможность преобразования данных из типа данных C к типу данных SQL или возвращается сообщение об ошибке. Список поддерживаемых преобразований см. в разделе [преобразование данных из C в типы данных SQL](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md) в типах данных приложение D:.  
  
-   Тип данных SQL, точность и Масштаб параметра.  
  
-   Адрес буфера длины и индикатора. Предоставляет байтовая длина двоичных или символьных данных, указывает, что данные имеют значение NULL или указывает, что данные будут отправляться с **SQLPutData**. Дополнительные сведения см. в разделе [использование значения длины/индикатора](../../../odbc/reference/develop-app/using-length-and-indicator-values.md).  
  
 Например, следующий код привязывает *менеджеров по продажам* и *CustID* параметров для менеджеров по продажам и CustID столбцов. Поскольку *менеджеров по продажам* содержит символьные данные переменной длины, в коде задается байтовая длина *менеджеров по продажам* (11) и привязывает *SalesPersonLenOrInd* для содержать байтовая длина данных в *менеджеров по продажам*. Эта информация не является обязательным для *CustID* , так как он содержит целочисленных данных имеет фиксированную длину.  
  
```  
SQLCHAR       SalesPerson[11];  
SQLINTEGER    SalesPersonLenOrInd, CustIDInd;  
SQLUINTEGER   CustID;  
  
// Bind SalesPerson to the parameter for the SalesPerson column and  
// CustID to the parameter for the CustID column.  
SQLBindParameter(hstmt1, 1, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_CHAR, 10, 0,  
                  SalesPerson, sizeof(SalesPerson), &SalesPersonLenOrInd);  
SQLBindParameter(hstmt1, 2, SQL_PARAM_INPUT, SQL_C_ULONG, SQL_INTEGER, 10, 0,  
                  &CustID, 0, &CustIDInd);  
  
// Set values of salesperson and customer ID and length/indicators.  
strcpy_s((char*)SalesPerson, _countof(SalesPerson), "Garcia");  
SalesPersonLenOrInd = SQL_NTS;  
CustID = 1331;  
CustIDInd = 0;  
  
// Execute a statement to get data for all orders made to the specified  
// customer by the specified salesperson.  
SQLExecDirect(hstmt1,"SELECT * FROM Orders WHERE SalesPerson=? AND CustID=?",SQL_NTS);  
```  
  
 Когда **SQLBindParameter** является именем, драйвер эти сведения хранятся в структуре для инструкции. При выполнении инструкции, он использует данные для получения данных параметра и отправлять их в источнике данных.  
  
> [!NOTE]  
>  В ODBC версии 1.0 параметры были связаны с **SQLSetParam**. Диспетчер драйверов сопоставляет вызовы между **SQLSetParam** и **SQLBindParameter**, в зависимости от версии используемого приложения и драйвер ODBC.

