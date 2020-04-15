---
title: Связывание параметрных маркеров Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: be99bc884a8baa66f3d632ee4731985f0cc85732
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306395"
---
# <a name="binding-parameter-markers"></a>Привязка маркеров параметров
Приложение связывает параметры, позвонив по **S'LBindParameter**. **S'LBindParameter** связывает один параметр за один раз. С его помощью приложение определяет следующее:  
  
-   Номер параметра. Параметры пронумеровались в увеличивающийся порядок параметра в выписке S'L, начиная с числа 1. Хотя законно указывать число параметров, превышающее число параметров в отчете S'L, значение параметра будет проигнорировано при выполнении оператора.  
  
-   Тип параметра (вход, вход/выход или выход). За исключением параметров в процедурных вызовах, все параметры являются входные параметры. Для получения дополнительной [информации,](../../../odbc/reference/develop-app/procedure-parameters.md)см Процедуры Параметры , позже в этом разделе.  
  
-   Тип данных C, адрес и длина байт переменной привязаны к параметру. Водитель должен быть в состоянии преобразовать данные из типа данных C в тип данных S'L или возвращается ошибка. Список поддерживаемых конверсий [можно](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md) узнать в приложении D: Типы данных.  
  
-   Тип данных, точность и масштаб самого параметра.  
  
-   Адрес буфера длины/индикатора. В нем приводится длина бинарных или характерных данных, указывается, что данные являются NULL, или указывается, что данные будут отправлены с **помощью S'LPutData.** Для получения дополнительной [информации см.](../../../odbc/reference/develop-app/using-length-and-indicator-values.md)  
  
 Например, следующий код связывает *SalesPerson* и *CustID* с параметрами для столбцов SalesPerson и CustID. Поскольку *SalesPerson* содержит данные о символах, которые имеют переменную длину, код определяет длину *байта SalesPerson* (11) и связывает *SalesPersonLenOrInd,* чтобы содержать длину данных в *SalesPerson.* Эта информация не является необходимой для *CustID,* поскольку она содержит множество данных, которые имеют фиксированную длину.  
  
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
  
 При вызове **S'LBindParameter** драйвер сохраняет эту информацию в структуре оператора. Когда выписка выполняется, она использует информацию для извлечения данных параметра и отправки ее в источник данных.  
  
> [!NOTE]  
>  В ODBC 1.0 параметры были связаны с **S'LSetParam**. Карты менеджера драйверов звонят между **S'LSetParam** и **S'LBindParameter**, в зависимости от версий ODBC, используемых приложением и драйвером.
