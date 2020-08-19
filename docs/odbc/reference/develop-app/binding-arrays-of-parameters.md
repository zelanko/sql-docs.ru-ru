---
description: Привязка массивов параметров
title: Привязка массивов параметров | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- binding parameter arrays [ODBC]
- arrays of parameter values [ODBC]
- parameter arrays [ODBC]
ms.assetid: 037afe23-052d-4f3a-8aa7-45302b199ad0
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 529ea49d2697ffcf7b89217746420ab5cb298890
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88429486"
---
# <a name="binding-arrays-of-parameters"></a>Привязка массивов параметров
Приложения, использующие массивы параметров, привязывают массив к параметрам в инструкции SQL. Существует два стиля привязки:  
  
-   Привяжите массив к каждому параметру. Каждая структура данных (array) содержит все данные для одного параметра. Это называется *привязкой на уровне столбца* , так как она привязывает столбец значений для одного параметра.  
  
-   Определите структуру для хранения данных параметров для всего набора параметров и привязки массива этих структур. Каждая структура данных содержит данные для одной инструкции SQL. Это называется *привязкой на уровне строк* , так как она привязывает строку параметров.  
  
 Как и когда приложение привязывает одну переменную к параметрам, оно вызывает **SQLBindParameter** для привязки массивов к параметрам. Единственное отличие состоит в том, что передаваемые адреса являются адресами массивов, а не однопеременными адресами. Приложение задает атрибут инструкции SQL_ATTR_PARAM_BIND_TYPE, чтобы указать, использует ли он столбец (по умолчанию) или привязку на уровне строк. Необходимость использования привязки на уровне столбца или строки в основном зависит от предпочтений приложения. В зависимости от того, как процессор получает доступ к памяти, привязка на уровне строк может выполняться быстрее. Однако это различие, скорее всего, будет незначительным, за исключением очень большого количества строк параметров.  
  
## <a name="column-wise-binding"></a>Привязка на уровне столбца  
 При использовании привязки на уровне столбца приложение привязывает один или два массива к каждому параметру, для которого должны быть предоставлены данные. Первый массив содержит значения данных, а второй массив содержит буферы длины или индикатора. Каждый массив содержит столько элементов, сколько есть значения для параметра.  
  
 По умолчанию используется привязка на уровне столбца. Приложение также может измениться с привязки на уровне строк к привязке по столбцам путем установки атрибута SQL_ATTR_PARAM_BIND_TYPE инструкции. На следующем рисунке показано, как работает привязка на уровне столбца.  
  
 ![Показывает, как работает привязка&#45;столбцов](../../../odbc/reference/develop-app/media/pr31.gif "pr31")  
  
 Например, следующий код привязывает 10-элементные массивы к параметрам для столбцов PartID, Description и Price и выполняет инструкцию для вставки 10 строк. Он использует привязку на уровне столбца.  
  
```  
#define DESC_LEN 51  
#define ARRAY_SIZE 10  
  
SQLCHAR *      Statement = "INSERT INTO Parts (PartID, Description,  Price) "  
                                                "VALUES (?, ?, ?)";  
SQLUINTEGER    PartIDArray[ARRAY_SIZE];  
SQLCHAR        DescArray[ARRAY_SIZE][DESC_LEN];  
SQLREAL        PriceArray[ARRAY_SIZE];  
SQLINTEGER     PartIDIndArray[ARRAY_SIZE], DescLenOrIndArray[ARRAY_SIZE],  
               PriceIndArray[ARRAY_SIZE];  
SQLUSMALLINT   i, ParamStatusArray[ARRAY_SIZE];  
SQLULEN ParamsProcessed;  
  
memset(DescLenOrIndArray, 0, sizeof(DescLenOrIndArray));  
memset(PartIDIndArray, 0, sizeof(PartIDIndArray));  
memset(PriceIndArray, 0, sizeof(PriceIndArray));  
  
// Set the SQL_ATTR_PARAM_BIND_TYPE statement attribute to use  
// column-wise binding.  
SQLSetStmtAttr(hstmt, SQL_ATTR_PARAM_BIND_TYPE, SQL_PARAM_BIND_BY_COLUMN, 0);  
  
// Specify the number of elements in each parameter array.  
SQLSetStmtAttr(hstmt, SQL_ATTR_PARAMSET_SIZE, ARRAY_SIZE, 0);  
  
// Specify an array in which to return the status of each set of  
// parameters.  
SQLSetStmtAttr(hstmt, SQL_ATTR_PARAM_STATUS_PTR, ParamStatusArray, 0);  
  
// Specify an SQLUINTEGER value in which to return the number of sets of  
// parameters processed.  
SQLSetStmtAttr(hstmt, SQL_ATTR_PARAMS_PROCESSED_PTR, &ParamsProcessed, 0);  
  
// Bind the parameters in column-wise fashion.  
SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_ULONG, SQL_INTEGER, 5, 0,  
                  PartIDArray, 0, PartIDIndArray);  
SQLBindParameter(hstmt, 2, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_CHAR, DESC_LEN - 1, 0,  
                  DescArray, DESC_LEN, DescLenOrIndArray);  
SQLBindParameter(hstmt, 3, SQL_PARAM_INPUT, SQL_C_FLOAT, SQL_REAL, 7, 0,  
                  PriceArray, 0, PriceIndArray);  
  
// Set part ID, description, and price.  
for (i = 0; i < ARRAY_SIZE; i++) {  
   GetNewValues(&PartIDArray[i], DescArray[i], &PriceArray[i]);  
   PartIDIndArray[i] = 0;  
   DescLenOrIndArray[i] = SQL_NTS;  
   PriceIndArray[i] = 0;  
}  
  
// Execute the statement.  
SQLExecDirect(hstmt, Statement, SQL_NTS);  
  
// Check to see which sets of parameters were processed successfully.  
for (i = 0; i < ParamsProcessed; i++) {  
   printf("Parameter Set  Status\n");  
   printf("-------------  -------------\n");  
   switch (ParamStatusArray[i]) {  
      case SQL_PARAM_SUCCESS:  
      case SQL_PARAM_SUCCESS_WITH_INFO:  
         printf("%13d  Success\n", i);  
         break;  
  
      case SQL_PARAM_ERROR:  
         printf("%13d  Error\n", i);  
         break;  
  
      case SQL_PARAM_UNUSED:  
         printf("%13d  Not processed\n", i);  
         break;  
  
      case SQL_PARAM_DIAG_UNAVAILABLE:  
         printf("%13d  Unknown\n", i);  
         break;  
  
   }  
}  
```  
  
## <a name="row-wise-binding"></a>Привязка на уровне строки  
 При использовании привязки на уровне строки приложение определяет структуру для каждого набора параметров. Структура содержит один или два элемента для каждого параметра. Первый элемент содержит значение параметра, а второй элемент содержит буфер длины или индикатора. Затем приложение выделяет массив этих структур, содержащий столько элементов, сколько значений для каждого параметра.  
  
 Приложение объявляет размер структуры драйверу с помощью атрибута SQL_ATTR_PARAM_BIND_TYPE оператора. Приложение привязывает адреса параметров в первой структуре массива. Таким образом, драйвер может вычислить адрес данных для конкретной строки и столбца, как  
  
```  
Address = Bound Address + ((Row Number - 1) * Structure Size) + Offset  
```  
  
 где нумерация строк выполняется от 1 до размера набора параметров. Смещение, если оно определено, является значением, на которое указывает атрибут оператора SQL_ATTR_PARAM_BIND_OFFSET_PTR. На следующем рисунке показано, как работает привязка на уровне строки. Параметры можно разместить в структуре в любом порядке, но они отображаются в последовательном порядке для ясности.  
  
 ![Показывает, как работает привязка&#45;к строке](../../../odbc/reference/develop-app/media/pr32.gif "pr32")  
  
 Следующий код создает структуру с элементами для значений, которые необходимо сохранить в столбцах PartID, Description и Price. Затем он выделяет 10-элементный массив этих структур и привязывает его к параметрам для столбцов PartID, Description и Price, используя привязку на уровне строк. Затем он выполняет инструкцию для вставки 10 строк.  
  
```  
#define DESC_LEN 51  
#define ARRAY_SIZE 10  
  
typedef tagPartStruct {  
   SQLREAL       Price;  
   SQLUINTEGER   PartID;  
   SQLCHAR       Desc[DESC_LEN];  
   SQLINTEGER    PriceInd;  
   SQLINTEGER    PartIDInd;  
   SQLINTEGER    DescLenOrInd;  
} PartStruct;  
  
PartStruct PartArray[ARRAY_SIZE];  
SQLCHAR *      Statement = "INSERT INTO Parts (PartID, Description,  
                Price) "  
               "VALUES (?, ?, ?)";  
SQLUSMALLINT   i, ParamStatusArray[ARRAY_SIZE];  
SQLULEN ParamsProcessed;  
  
// Set the SQL_ATTR_PARAM_BIND_TYPE statement attribute to use  
// column-wise binding.  
SQLSetStmtAttr(hstmt, SQL_ATTR_PARAM_BIND_TYPE, sizeof(PartStruct), 0);  
  
// Specify the number of elements in each parameter array.  
SQLSetStmtAttr(hstmt, SQL_ATTR_PARAMSET_SIZE, ARRAY_SIZE, 0);  
  
// Specify an array in which to return the status of each set of  
// parameters.  
SQLSetStmtAttr(hstmt, SQL_ATTR_PARAM_STATUS_PTR, ParamStatusArray, 0);  
  
// Specify an SQLUINTEGER value in which to return the number of sets of  
// parameters processed.  
SQLSetStmtAttr(hstmt, SQL_ATTR_PARAMS_PROCESSED_PTR, &ParamsProcessed, 0);  
  
// Bind the parameters in row-wise fashion.  
SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_ULONG, SQL_INTEGER, 5, 0,  
                  &PartArray[0].PartID, 0, &PartArray[0].PartIDInd);  
SQLBindParameter(hstmt, 2, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_CHAR, DESC_LEN - 1, 0,  
                  PartArray[0].Desc, DESC_LEN, &PartArray[0].DescLenOrInd);  
SQLBindParameter(hstmt, 3, SQL_PARAM_INPUT, SQL_C_FLOAT, SQL_REAL, 7, 0,  
                  &PartArray[0].Price, 0, &PartArray[0].PriceInd);  
  
// Set part ID, description, and price.  
for (i = 0; i < ARRAY_SIZE; i++) {  
   GetNewValues(&PartArray[i].PartID, PartArray[i].Desc, &PartArray[i].Price);  
   PartArray[0].PartIDInd = 0;  
   PartArray[0].DescLenOrInd = SQL_NTS;  
   PartArray[0].PriceInd = 0;  
}  
  
// Execute the statement.  
SQLExecDirect(hstmt, Statement, SQL_NTS);  
  
// Check to see which sets of parameters were processed successfully.  
for (i = 0; i < ParamsProcessed; i++) {  
   printf("Parameter Set  Status\n");  
   printf("-------------  -------------\n");  
   switch (ParamStatusArray[i]) {  
      case SQL_PARAM_SUCCESS:  
      case SQL_PARAM_SUCCESS_WITH_INFO:  
         printf("%13d  Success\n", i);  
         break;  
  
      case SQL_PARAM_ERROR:  
         printf("%13d  Error\n", i);  
         break;  
  
      case SQL_PARAM_UNUSED:  
         printf("%13d  Not processed\n", i);  
         break;  
  
      case SQL_PARAM_DIAG_UNAVAILABLE:  
         printf("%13d  Unknown\n", i);  
         break;  
  
   }  
```
