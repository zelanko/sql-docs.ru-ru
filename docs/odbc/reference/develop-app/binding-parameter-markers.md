---
title: Привязка маркеров параметров | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- parameter markers [ODBC]
- binding parameter markers [ODBC]
ms.assetid: fe88c1c2-4ee4-45e0-8500-b8c25c047815
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c71967bd72f7f13a725d47517cb9e66eee7da87f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63199392"
---
# <a name="binding-parameter-markers"></a>Привязка маркеров параметров
Приложение выполняет привязку параметров, вызвав **SQLBindParameter**. **SQLBindParameter** привязывает один параметр за раз. С ее помощью приложение указывает следующее:  
  
-   Номер параметра. Параметры нумеруются в порядке возрастания параметра в инструкции SQL, начиная с номера 1. Хотя можно задать параметр с номером, который больше, чем число параметров в инструкции SQL, значение параметра будут игнорироваться при выполнении инструкции.  
  
-   Параметр типа (входной, ввода вывода, или вывести). За исключением параметров в вызовах процедуры все параметры являются входными параметрами. Дополнительные сведения см. в разделе [параметров процедуры](../../../odbc/reference/develop-app/procedure-parameters.md)далее в этом разделе.  
  
-   C данных тип, адрес и байтов длина переменной, привязанного к параметру. Драйвер должен иметь возможность преобразовать данные из типа данных C к типу данных SQL или будет возвращена ошибка. Список поддерживаемых преобразований, см. в разделе [преобразование данных из C в типы данных SQL](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md) в приложение г Типы данных.  
  
-   Тип данных SQL, точность и Масштаб параметра.  
  
-   Адрес буфера длины и индикатора. Он предоставляет байтовая длина двоичных или символьных данных, указывает, что данные имеют значение NULL или указывает, что данные будут отправлены с **SQLPutData**. Дополнительные сведения см. в разделе [использование значений длины и индикатора](../../../odbc/reference/develop-app/using-length-and-indicator-values.md).  
  
 Например, следующий код привязывает *менеджеров по продажам* и *CustID* к параметрам для менеджеров по продажам и CustID столбцов. Так как *менеджеров по продажам* содержит символьные данные, которая является переменной длины, код задает длину в байтах *менеджеров по продажам* (11) и привязывает *SalesPersonLenOrInd* для содержать байтовая длина данных в *менеджеров по продажам*. Эта информация не является обязательным для *CustID* так как она содержит целочисленные данные, который является фиксированной длины.  
  
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
  
 Когда **SQLBindParameter** является именем, драйвер эти сведения хранятся в структуре для инструкции. При выполнении инструкции, в нем сведения для получения данных параметра и отправить его в источник данных.  
  
> [!NOTE]  
>  В ODBC 1.0 параметры были связаны с **SQLSetParam**. Диспетчер драйверов сопоставляет вызовы между **SQLSetParam** и **SQLBindParameter**, в зависимости от версии используемых приложений и драйверов ODBC.
