---
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 76f756b96a62a174e329614f9ab1baf634937522
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63199644"
---
# <a name="binding-arrays-of-parameters"></a>Привязка массивов параметров
Приложения, использующие массивов параметров связать массивы параметров в инструкции SQL. Существует два стиля привязки:  
  
-   Привязать массив для каждого параметра. Каждая структура данных (array) содержит все данные для одного параметра. Это называется *привязка на уровне столбцов* так, как он выполняет привязку столбца значений для одного параметра.  
  
-   Определите структуру для хранения данных параметра для всего набора параметров и привязать массив этих структур. Каждая структура данных содержит данные для отдельной инструкции SQL. Это называется *привязку на уровне строки* так, как он выполняет привязку ряд параметров.  
  
 Если приложение связывает один переменные с параметрами, он не вызывает **SQLBindParameter** чтобы связать массивы параметров. Единственным различием является переданных адресов адреса массива, не одной переменной. Приложение устанавливает атрибут SQL_ATTR_PARAM_BIND_TYPE инструкции, чтобы указать, является ли использование на уровне столбца (по умолчанию) или привязка на уровне строки. Следует ли использовать привязки на уровне столбца или на уровне строки — это во многом вопрос предпочтений приложения. В зависимости от того, как процессор получает доступ к памяти привязка на уровне строки могут выполняться быстрее. Тем не менее разница скорее всего, можно пренебречь, за исключением очень большое количество строк параметров.  
  
## <a name="column-wise-binding"></a>Привязка на уровне столбца  
 При использовании привязки на уровне столбца, приложение привязывает один или два массива для каждого параметра, для которого будет предоставляться данных. Первый массив содержит значения данных, а второй массив содержит буфер длины/индикатора. Каждый массив содержит столько элементов, сколько существует значений для параметра.  
  
 Привязка на уровне столбца по умолчанию. Приложение также можно изменить привязку на уровне строки для привязки на уровне столбца, присвоив атрибуту SQL_ATTR_PARAM_BIND_TYPE инструкции. На следующем рисунке показано, на уровне столбца работает привязки.  
  
 ![Показано, как столбец&#45;с точки зрения происходит связывание](../../../odbc/reference/develop-app/media/pr31.gif "pr31")  
  
 Например следующий код связывает 10-элементные массивы параметров для столбцов PartID, описание и цена и выполняет инструкцию, чтобы вставить 10 строк. В нем используется привязка на уровне столбца.  
  
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
 Если вы используете привязку на уровне строки, приложение определяет структуру для каждого набора параметров. Эта структура содержит один или два элемента для каждого параметра. Первый элемент содержит значение параметра, а второй элемент содержит буфер длины/индикатора. Затем приложение выделяет массив этих структур, содержащий столько элементов, сколько существует значений для каждого параметра.  
  
 Приложение объявляет размер структуры для драйвера с SQL_ATTR_PARAM_BIND_TYPE атрибут инструкции. Приложение выполняет привязку адреса параметров в структуре первого массива. Таким образом драйвер можно вычислить адрес данных для конкретной строки и столбца в виде  
  
```  
Address = Bound Address + ((Row Number - 1) * Structure Size) + Offset  
```  
  
 где строк пронумерованы от 1 до размера набор параметров. Смещение, если определено, является значением, на которые указывают атрибут SQL_ATTR_PARAM_BIND_OFFSET_PTR инструкции. На следующем рисунке показано, на уровне строки работает привязки. Параметры можно поместить в структуре в любом порядке, но отображаются в последовательном порядке для ясности.  
  
 ![Показано, как строка&#45;с точки зрения происходит связывание](../../../odbc/reference/develop-app/media/pr32.gif "pr32")  
  
 Следующий код создает структуру с элементами для значений для хранения в столбцах PartID, описание и цена. Затем он выделяет массив из 10 элементов этих структур и привязывает его к параметрам для столбцов PartID, описание и цена, используя привязку на уровне строки. Затем выполняется инструкция insert 10 строк.  
  
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
