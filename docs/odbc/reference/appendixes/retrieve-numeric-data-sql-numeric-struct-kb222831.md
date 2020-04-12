---
title: Извлекать числовые данные с помощью SQL_NUMERIC_STRUCT Документы Майкрософт
description: С/КЗ с помощью ODBC извлекает тип цифровых данных сервера S'L, используя SQL_NUMERIC_STRUCT, связанные с SQL_C_NUMERIC.
editor: ''
ms.prod: sql
ms.technology: connectivity
ms.devlang: cpp
ms.topic: conceptual
ms.custom: ''
ms.date: 07/14/2017
ms.author: genemi
author: MightyPen
ms.openlocfilehash: ec2b68b918cbc79a245fe639108e94165be729c8
ms.sourcegitcommit: 54cfeb36c9caa51ec68fa8f4a1918e305db5e00a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/11/2020
ms.locfileid: "81219103"
---
# <a name="retrieve-numeric-data-with-sql_numeric_struct"></a>Извлекать числовые\_данные\_с помощью СЗЛ НУМЕРИК СТРУКТ

В этой статье описывается, как получить числовые данные из драйвера ODBC сервера S'L в числовую структуру. В нем также описывается, как получить правильные значения, используя определенные значения точности и масштаба.

Этот тип данных позволяет приложениям непосредственно обрабатывать числовые данные. Примерно в 2003 году ODBC 3.0 представил новый тип данных ODBC C, идентифицированный **СЗЛ\_\_C NUMERIC**. Этот тип данных по-прежнему актуален по состоянию на 2017 год.

Используемый буфер C имеет определение типа **S'L\_NUMERIC\_STRUCT.** Эта структура имеет поля для хранения точности, масштаба, знака и значения численных данных. Само значение хранится в виде масштабирования целых с наименее значительным байтом, начинающимся в левом положении. 

В статье [C Data Types](c-data-types.md) содержится более подробная информация о формате и использовании СЗЛ\_NUMERIC\_STRUCT. Как правило, в [приложении D](appendix-d-data-types.md) от справки программиста ODBC 3.0 рассматриваются типы данных.


## <a name="sql_numeric_struct-overview"></a>Обзор\_СЗЛ-НУМЕРИК\_СТРУКТ


Заголовок\_s'L NUMERIC\_STRUCT определяется в файле заголовка sqltypes.h следующим образом:


```c
#define SQL_MAX_NUMERIC_LEN    16
typedef struct tagSQL_NUMERIC_STRUCT
{
   SQLCHAR    precision;
   SQLSCHAR   scale;
   SQLCHAR    sign;   /* 1 if positive, 0 if negative */
   SQLCHAR    val[SQL_MAX_NUMERIC_LEN];
} SQL_NUMERIC_STRUCT;
```

            
Поля точности и масштаба численной структуры никогда не используются для ввода из приложения, только для вывода от драйвера к приложению.

При возвращении данных в приложение драйвер использует точность по умолчанию (определенную драйвером) и шкалу по умолчанию (0). Если приложение не определяет значения точности и масштаба, драйвер принимает значение по умолчанию и усечения десятичной части численных данных.

## <a name="sql_numeric_struct-code-sample"></a>Образец\_кода\_СЗЛ НУМЕРИК СТРУКТ

Этот пример кода показывает, как:

- Установите точность.
- Установите шкалу.
- Извлекайте правильные значения. 

> [!Note]
> ЛЮБОЕ ИСПОЛЬЗОВАНИЕ ВАМИ КОДА, ПРЕДУСМОТРЕННОГО В ДАННОЙ СТАТЬЕ, НА СВОЙ СТРАХ И РИСК. 
>
> Корпорация Майкрософт предоставляет эти образцы кода "как есть" без гарантии любого рода, либо выраженные или подразумеваемые, в том числе, но не ограничиваясь подразумеваемыми гарантиями товарности и/или пригодности для конкретной цели.

```c
#include <stdio.h>
#include <string.h>
#include <conio.h>
#include <stdlib.h>
#include <ctype.h>
#include <windows.h>
#include <sql.h>
#include <sqlext.h>

#define MAXDSN       25
#define MAXUID       25
#define MAXAUTHSTR   25
#define MAXBUFLEN   255

SQLHENV     henv   = SQL_NULL_HENV;
SQLHDBC     hdbc1  = SQL_NULL_HDBC;     
SQLHSTMT    hstmt1 = SQL_NULL_HSTMT;
SQLHDESC    hdesc  = NULL;


SQL_NUMERIC_STRUCT NumStr;

int main()
{
   RETCODE retcode;

//Change the values below as appropriate to make a successful connection.
//szDSN: DataSourceName, szUID=userid, szAuthStr: password

UCHAR szDSN[MAXDSN+1] = "sql33",szUID[MAXUID+1]="sa", szAuthStr[MAXAUTHSTR+1] = "";
SQLINTEGER strlen1;
SQLINTEGER a;
int i,sign =1;
long myvalue, divisor;
float final_val;
   
// Allocate the Environment handle. Set the Env attribute, allocate the
//connection handle, connect to the database and allocate the statement //handle.

retcode = SQLAllocHandle (SQL_HANDLE_ENV, NULL, &henv);
retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION,(SQLPOINTER) SQL_OV_ODBC3, SQL_IS_INTEGER);
retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc1);
retcode = SQLConnect(hdbc1, szDSN,SQL_NTS,szUID,SQL_NTS,szAuthStr,SQL_NTS);
retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt1);

// Execute the select statement. Here it is assumed that numeric_test
//table is created using the following statements:

// Create table numeric_test (col1 numeric(5,3))
//insert into numeric_test values (25.212)

retcode = SQLExecDirect(hstmt1,(UCHAR *)"select * from numeric_test",SQL_NTS);

// Use SQLBindCol to bind the NumStr to the column that is being retrieved.

retcode = SQLBindCol(hstmt1,1,SQL_C_NUMERIC,&NumStr,19,&strlen1);

// Get the application row descriptor for the statement handle using
//SQLGetStmtAttr.

retcode = SQLGetStmtAttr(hstmt1, SQL_ATTR_APP_ROW_DESC,&hdesc, 0, NULL);

// You can either use SQLSetDescRec or SQLSetDescField when using
// SQLBindCol. However, if you prefer to call SQLGetData, you have to
// call SQLSetDescField instead of SQLSetDescRec. For more information on
// descriptors, please refer to the ODBC 3.0 Programmers reference or
// your Online documentation.

//Used when using SQLSetDescRec
//a=b=sizeof(NumStr);

// Set the datatype, precision and scale fields of the descriptor for the 
//numeric column. Otherwise the default precision (driver defined) and 
//scale (0) are returned.

// In this case, the table contains only one column, hence the second 
//parameter contains one. Zero applies to bookmark columns. Please check 
//the programmers guide for more information.

//retcode=SQLSetDescRec(hdesc,1,SQL_NUMERIC,NULL,sizeof(NumStr),5,3,&NumStr,&a,&b);

retcode = SQLSetDescField (hdesc,1,SQL_DESC_TYPE,(VOID*)SQL_C_NUMERIC,0);
retcode = SQLSetDescField (hdesc,1,SQL_DESC_PRECISION,(VOID*) 5,0);
retcode = SQLSetDescField (hdesc,1,SQL_DESC_SCALE,(VOID*) 3,0);
    
// Initialize the val array in the numeric structure.

memset(NumStr.val,0,16);
   
// Call SQLFetch to fetch the first record.

while((retcode =SQLFetch(hstmt1)) != SQL_NO_DATA)
  {
// Notice that the TargetType (3rd Parameter) is SQL_ARD_TYPE, which  
//forces the driver to use the Application Row Descriptor with the 
//specified scale and precision.

   retcode = SQLGetData(hstmt1, 1, SQL_ARD_TYPE, &NumStr, 19, &a); 

// Check for null indicator.

   if ( SQL_NULL_DATA == a )
   {
   printf( "The final value: NULL\n" );
   continue;
   }

// Call to convert the little endian mode data into numeric data.

   myvalue = strtohextoval();

// The returned value in the above code is scaled to the value specified
//in the scale field of the numeric structure. For example 25.212 would
//be returned as 25212. The scale in this case is 3 hence the integer 
//value needs to be divided by 1000.

   divisor = 1;
   if(NumStr.scale > 0)
     {
    for (i=0;i< NumStr.scale; i++)   
         divisor = divisor * 10;
     }
   final_val =  (float) myvalue /(float) divisor;

// Examine the sign value returned in the sign field for the numeric
//structure.
//NOTE: The ODBC 3.0 spec required drivers to return the sign as 
//1 for positive numbers and 2 for negative number. This was changed in the
//ODBC 3.5 spec to return 0 for negative instead of 2.

      if(!NumStr.sign) sign = -1;
      else sign  =1;

   final_val *= sign;
   printf("The final value: %f\n",final_val);
    }

   while ( ( retcode = SQLMoreResults(hstmt1) ) != SQL_NO_DATA_FOUND);

   /* clean up */ 
   SQLFreeHandle(SQL_HANDLE_STMT, hstmt1);
   SQLDisconnect(hdbc1);
   SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);
   SQLFreeHandle(SQL_HANDLE_ENV, henv);
   return(0);
}
```


### <a name="interim-results"></a>Промежуточные результаты:


```console
//  C  ==> 12 * 1    =     12
//  7  ==> 07 * 16   =    112
//  2  ==> 02 * 256  =    512
//  6  ==> 06 * 4096 =  24576
===============================
                 Sum =  25212
```


В численной структуре поле val представляет собой набор символов из 16 элементов. Например, 25.212 масштабируется до 25212, а шкала 3. В гексадецимальном формате это число будет 627C.

Водитель возвращает следующие элементы:

- Эквивалентный символ 7C, который является '' (труба) в первом элементе массива символов.
- Эквивалент 62, что является 'b' во втором элементе.
- Остатки элементов массива содержат нули, поэтому буфер содержит ''b'0'.

Теперь задача состоит в том, чтобы построить масштабируемую целостную часть из этого массива строки. Каждый символ в строке соответствует двум гексадецимальным цифрам, не говоря уже о наименее значимой цифре (LSD) и наиболее значительной цифре (MSD). Масштабируемое значение рядов может быть сгенерировано путем умножения каждой цифры (LSD & MSD) с кратным 16, начиная с 1.

Код, который реализует преобразование из маленького эндианского режима в масштабированный штат. Реализовать эту функцию должен разработчик приложения. Следующий пример кода является лишь одним из многих возможных способов.


```c
long strtohextoval()
{
    long val=0,value=0;
    int i=1,last=1,current;
    int a=0,b=0;

        for(i=0;i<=15;i++)
        {
         current = (int) NumStr.val[i];
         a= current % 16; //Obtain LSD
         b= current / 16; //Obtain MSD
            
         value += last* a;   
         last = last * 16;   
         value += last* b;
         last = last * 16;   
        }
     return value;
}
```


### <a name="applies-to-versions"></a>Применяется к версиям


Предыдущая информация\_о\_S'L NUMERIC STRUCT относится к следующим версиям продукта:

- Драйвер Microsoft ODBC для Microsoft S'L Server 3.7
- Компоненты доступа к данным Майкрософт 2.1
- Компоненты доступа к данным Майкрософт 2.5
- Компоненты доступа к данным Майкрософт 2.6
- Компоненты доступа к данным Майкрософт 2.7


## <a name="sql_c_numeric-overview"></a>Обзор\_СЗЛ C\_NUMERIC


Следующая примерная программа иллюстрирует использование\_\_S'L C NUMERIC, вставив 123,45 в таблицу. В таблице столбец определяется как числовая или десятичная, с точностью 5 и с шкалой 2.

Драйвер ODBC, который вы используете для запуска этой программы, должен поддерживать функциональность ODBC 3.0.


```c
#include <windows.h>
#include <sql.h>
#include <sqlext.h>

void main() {

   SQLHENV    henv  = NULL;
   SQLHDBC    hdbc  = NULL;
   SQLHSTMT   hstmt = NULL;

   SQL_NUMERIC_STRUCT   NumStr;
   SQLINTEGER           cbNumStr = sizeof (NumStr);

   SQLAllocHandle(SQL_HANDLE_ENV, NULL, &henv);

   /* Set the ODBC behavior version. */ 
   SQLSetEnvAttr(henv,
         SQL_ATTR_ODBC_VERSION,
         (SQLPOINTER) SQL_OV_ODBC3,
         SQL_IS_INTEGER);

   SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);

   /* Substitute your own connection information */ 
   SQLConnect(hdbc,
      (SQLCHAR *) "MyDSN", 5,
      (SQLCHAR *) "UserID", 6,
      (SQLCHAR *) "Password", 8);

   SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt);

   /*
      Set up the SQL_NUMERIC_STRUCT, NumStr, to hold "123.45".

      First, we need to scale 123.45 to an integer: 12345
      One way to switch the bytes is to convert 12345 to Hex:  0x3039
      Since the least significant byte will be stored starting from the
      leftmost byte, "0x3039" will be stored as "0x3930".

      The precision and scale fields are not used for input to the driver,
      only for output from the driver. The precision and scale will be set
      in the application parameter descriptor later.
   */ 

   NumStr.sign = 1;   /* 1 if positive, 2 if negative */ 

   memset (NumStr.val, 0, 16);
   NumStr.val [0] = 0x39;
   NumStr.val [1] = 0x30;

   /* SQLBindParameter needs to be called before SQLSetDescField */ 
   SQLBindParameter(hstmt,
          1,
          SQL_PARAM_INPUT,
          SQL_C_NUMERIC,
          SQL_NUMERIC,
          5,
          2,
          &NumStr,
          0,
          (SQLINTEGER *) &cbNumStr);

   /* Modify the fields in the implicit application parameter descriptor */ 
   SQLHDESC   hdesc = NULL;

   SQLGetStmtAttr(hstmt, SQL_ATTR_APP_PARAM_DESC, &hdesc, 0, NULL);
   SQLSetDescField(hdesc, 1, SQL_DESC_TYPE, (SQLPOINTER) SQL_C_NUMERIC, 0);
   SQLSetDescField(hdesc, 1, SQL_DESC_PRECISION, (SQLPOINTER) 5, 0);
   SQLSetDescField(hdesc, 1, SQL_DESC_SCALE, (SQLPOINTER) 2, 0);
   SQLSetDescField(hdesc, 1, SQL_DESC_DATA_PTR, (SQLPOINTER) &NumStr, 0);

   SQLExecDirect(hstmt,
         (SQLCHAR *) "INSERT INTO table (numeric_column) VALUES (?)",
         SQL_NTS);

   SQLFreeHandle(SQL_HANDLE_STMT, hstmt);

   SQLDisconnect (hdbc);

   SQLFreeHandle(SQL_HANDLE_DBC, hdbc);
   SQLFreeHandle(SQL_HANDLE_ENV, henv);
}
```


<!--
GeneMi historical notes, 2017/July/12. Per Jason.C

https://go.microsoft.com/fwlink/?LinkId=147596

https://support.microsoft.com/help/222831

https://web.archive.org/web/20140319133434/http:/support.microsoft.com:80/kb/222831

https://web.archive.org/web/20080505073901/http:/support.microsoft.com:80/kb/181254

https://docs.microsoft.com/sql/odbc/reference/appendixes/c-data-types
-->

