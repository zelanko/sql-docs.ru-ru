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
ms.openlocfilehash: 0e625e01b9bf4771f18dd8e9807ab09100ca580c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68107651"
---
# <a name="binding-parameter-markers"></a>Привязка маркеров параметров
Приложение привязывает параметры путем вызова **SQLBindParameter**. **SQLBindParameter** привязывает один параметр за раз. В нем в приложении указано следующее:  
  
-   Номер параметра. Параметры нумеруются в порядке возрастания параметров в инструкции SQL, начиная с номера 1. Хотя допустимо указывать номер параметра, превышающий число параметров в инструкции SQL, значение параметра будет игнорироваться при выполнении инструкции.  
  
-   Тип параметра (input, Input/Output или Output). За исключением параметров в вызовах процедур, все параметры являются входными параметрами. Дополнительные сведения см. Далее в подразделе [Параметры процедуры](../../../odbc/reference/develop-app/procedure-parameters.md).  
  
-   Тип данных C, адрес и длина байта переменной, привязанной к параметру. Драйвер должен иметь возможность преобразования данных из типа данных C в тип данных SQL, иначе возвращается ошибка. Список поддерживаемых преобразований см. в разделе [Преобразование данных из C в типы данных SQL](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md) в приложении г: типы данных.  
  
-   Тип данных SQL, точность и масштаб самого параметра.  
  
-   Адрес буфера длины или индикатора. Он предоставляет длину в байтах двоичных или символьных данных, указывает, что данные будут иметь значение NULL, или указывает, что данные отправляются с помощью **SQLPutData**. Дополнительные сведения см. [в разделе Использование значений длины и индикатора](../../../odbc/reference/develop-app/using-length-and-indicator-values.md).  
  
 Например, следующий код привязывает *SalesPerson* и *CustID* к параметрам для столбцов SalesPerson и CustID. Так как *Продавец* содержит символьные данные, которые имеют переменную длину, код определяет длину в байтах для *продавца* (11) и привязывает *салесперсонленоринд* , чтобы вместить длину байт данных в *менеджере по продажам*. Эта информация не является обязательной для объекта *CustID* , так как содержит целочисленные данные с фиксированной длиной.  
  
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
  
 При вызове **SQLBindParameter** драйвер сохраняет эти сведения в структуре для инструкции. При выполнении инструкции она использует информацию для получения данных параметров и отправляет их в источник данных.  
  
> [!NOTE]  
>  В ODBC 1,0 параметры были привязаны с помощью **SQLSetParam**. Диспетчер драйверов сопоставляет вызовы между **SQLSetParam** и **SQLBindParameter**в зависимости от версий ODBC, используемых приложением и драйвером.
