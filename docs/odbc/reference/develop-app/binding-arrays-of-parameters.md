---
title: Связывание массивов параметров Документы Майкрософт
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
ms.openlocfilehash: 73cfcde89e89edb87a4955cf0854c66a01d81e6f
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81283424"
---
# <a name="binding-arrays-of-parameters"></a>Привязка массивов параметров
Приложения, использовавшие массивы параметров, связывают массивы с параметрами в отчете S'L. Существует два стиля связывания:  
  
-   Привязать массив к каждому параметру. Каждая структура данных (массив) содержит все данные по одному параметру. Это называется *связыванием с характерю столбцов,* поскольку он связывает столбец значений для одного параметра.  
  
-   Определите структуру для хранения данных параметров для всего набора параметров и привязать массив этих структур. Каждая структура данных содержит данные для одного оператора S'L. Это называется *связыванием по гребню,* поскольку он связывает ряд параметров.  
  
 Наряду с тем, что приложение связывает отдельные переменные с параметрами, оно вызывает **S'LBindParameter,** чтобы связать массивы с параметрами. Разница лишь в том, что пройдены адреса являются адресами массива, а не однопеременными. Приложение устанавливает атрибут SQL_ATTR_PARAM_BIND_TYPE оператора, чтобы указать, использует ли он связывание столбцов (по умолчанию) или связывание по строке. Использование связывания с характерю столбцов или строки в основном является вопросом предпочтений приложения. В зависимости от того, как процессор получает доступ к памяти, связывание между строками может быть более быстрым. Однако разница, вероятно, будет незначительной, за исключением очень большого количества рядов параметров.  
  
## <a name="column-wise-binding"></a>Привязка на уровне столбца  
 При использовании связывания с использованием столбцов приложение связывает один или два массива с каждым параметром, по которому должны предоставляться данные. Первый массив содержит значения данных, а второй массив содержит буферы длины/индикатора. Каждый массив содержит столько элементов, сколько значений для параметра.  
  
 Связывание по колонке по умолчанию. Приложение также может изменяться от привязки с роутной строкой к связыванию с характерной для столбцов, установив атрибут SQL_ATTR_PARAM_BIND_TYPE оператора. Следующая иллюстрация показывает, как работает связывание с характером столбца.  
  
 ![Показывает, как работает столбец&#45;мудрый привязка](../../../odbc/reference/develop-app/media/pr31.gif "pr31")  
  
 Например, следующий код связывает 10-элементные массивы с параметрами для столбцов PartID, Description и Price и выполняет инструкцию для вставки 10 строк. Он использует столбец-мудрый связывая.  
  
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
 При использовании связывания с рядом приложение определяет структуру для каждого набора параметров. Структура содержит один или два элемента для каждого параметра. Первый элемент содержит значение параметра, а второй элемент содержит буфер длины/индикатора. Затем приложение выделяет массив этих структур, который содержит столько элементов, сколько есть значения для каждого параметра.  
  
 Приложение декларирует размер конструкции водителю с атрибутом SQL_ATTR_PARAM_BIND_TYPE оператора. Приложение связывает адреса параметров в первой структуре массива. Таким образом, водитель может вычислить адрес данных для определенной строки и столбца как  
  
```  
Address = Bound Address + ((Row Number - 1) * Structure Size) + Offset  
```  
  
 где строки пронумерования от 1 до размера набора параметров. Смещение, если она определена, является значением, на который указывает атрибут SQL_ATTR_PARAM_BIND_OFFSET_PTR оператора. Следующая иллюстрация показывает, как работает связывание между строками. Параметры могут быть помещены в структуру в любом порядке, но показаны в последовательном порядке для ясности.  
  
 ![Показывает, как работает строка&#45;мудрый связывание](../../../odbc/reference/develop-app/media/pr32.gif "pr32")  
  
 Следующий код создает структуру с элементами для хранения значений в столбцах PartID, Описание и Цена. Затем он выделяет 10-элементный массив этих структур и связывает его с параметрами для столбцов PartID, Описания и Цены, используя связывание по гребню. Затем выполняется заявление для вставки 10 строк.  
  
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
