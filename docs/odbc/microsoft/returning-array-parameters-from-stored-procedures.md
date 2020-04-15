---
title: Возвращающиеся параметры массива из сохраненных процедур Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- stored procedures [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], stored procedures
ms.assetid: 2018069b-da5d-4cee-a971-991897d4f7b5
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bc998dadc0e0c4a4bfe054bfd1d40296bc176393
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81292864"
---
# <a name="returning-array-parameters-from-stored-procedures"></a>Возврат параметров массива из хранимых процедур
> [!IMPORTANT]  
>  Эта функция будет удалена в будущей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставленный Oracle.  
  
 В Oracle 7.3 нет возможности получить доступ к типу записи PL/S'L, за исключением программы PL/S'L. Если упакованная процедура или функция имеет формальный аргумент, определяемый как тип записи PL/S'L, невозможно связать этот формальный аргумент в качестве параметра. Используйте тип PL/S'L TABLE в драйвере Microsoft ODBC для Oracle, чтобы вызвать параметры массива из процедур, содержащих правильные последовательности побега.  
  
 Чтобы вызвать процедуру, используйте следующий синтаксис:  
  
```  
{call  <package-name>.<proc-or-func>;  
(..., {resultset <max-records-requested> ,<formal-array-param_1>,;  
 <formal-array-param_2>,...,<formal-array-param_n> }, ... ) }  
```  
  
> [!NOTE]  
>  Запрошенный \<максимальный> параметр должен быть больше или равен количеству строк, присутствующих в наборе результатов. В противном случае Oracle возвращает ошибку, которая передается пользователю водителем.  
>   
>  Записи PL/S'L не могут использоваться в качестве параметров массива. Каждый параметр массива может представлять только одну колонку таблицы баз данных.  
  
 В следующем примере определяется пакет, содержащий два процедуры, которые возвращают разные наборы результатов, а затем предоставляется два способа возврата наборов результатов из пакета.  
  
## <a name="package-definition"></a>Определение пакета:  
  
```  
CREATE OR REPLACE PACKAGE SimplePackage AS  
  
TYPE t_id is TABLE of  NUMBER(5)  
    INDEX BY BINARY_INTEGER;  
  
TYPE t_Course is TABLE of VARCHAR2(10)  
    INDEX BY BINARY_INTEGER;  
  
TYPE t_Dept is TABLE of VARCHAR2(5)  
    INDEX BY BINARY_INTEGER;  
  
PROCEDURE proc1  
   (  
   o_id             OUT    t_id,  
   ao_course       OUT    t_Course,  
   ao_dept         OUT    t_Dept  
   );  
  
TYPE t_pk1Type1 IS TABLE OF VARCHAR2(100) INDEX BY BINARY_INTEGER;  
TYPE t_pk1Type2 IS TABLE OF NUMBER INDEX BY BINARY_INTEGER;  
PROCEDURE proc2  
   (  
   i_Arg1         IN    NUMBER,  
   ao_Arg2         OUT   t_pk1Type1,  
   ao_Arg3         OUT   t_pk1Type2  
   );  
  
END SimplePackage;  
  
CREATE OR REPLACE PACKAGE BODY SimplePackage AS  
    PROCEDURE  proc1 ( o_id OUT t_id,  
    ao_course OUT t_Course, ao_dept OUT t_Dept   ) AS  
    BEGIN  
          o_id(1):= 200;  
          ao_course(1) :=  'M101';  
          ao_dept(1) :=  'EEE' ;  
  
          o_id(2) := 201;  
          ao_course(2) :=  'PHY320';  
          ao_dept(2) :=  'ECE' ;  
  
     END proc1;  
PROCEDURE proc2  
   (  
   i_Arg1         IN    NUMBER,  
   ao_Arg2         OUT   t_pk1Type1,  
   ao_Arg3         OUT   t_pk1Type2  
   )  
AS  
   i   NUMBER;  
BEGIN  
   FOR i IN 1 .. i_Arg1 LOOP  
      ao_Arg2(i) := 'Row Number ' || to_char(i);  
   END LOOP;  
   FOR i IN 1 .. i_Arg1 LOOP  
      ao_Arg3(i) := i;  
   END LOOP;  
END proc2;  
END SimplePackage;  
```  
  
#### <a name="to-invoke-procedure-proc1"></a>Для выдвижения процедуры PROC1  
  
1.  Верните все столбцы в одном наборе результатов:  
  
    ```  
    {call SimplePackage.Proc1( {resultset  3, o_id , ao_course, ao_dept  } ) }  
    ```  
  
2.  Верните каждый столбец в виде единого набора результатов:  
  
    ```  
    {call SimplePackage.Proc1( {resultset 3, o_id},  {resultset 3, ao_course}, {resultset 3, ao_dept} ) }  
    ```  
  
     Это возвращает три набора результатов, по одному для каждого столбца.  
  
#### <a name="to-invoke-procedure-proc2"></a>Для выдвижения процедуры PROC2  
  
1.  Верните все столбцы в одном наборе результатов:  
  
    ```  
    {call SimplePackage.Proc2( 5 , {resultset  5, ao_Arg2, ao_Arg3} ) }  
    ```  
  
2.  Верните каждый столбец в виде единого набора результатов:  
  
    ```  
    {call SimplePackage.Proc2( 5 , {resultset 5, ao_Arg2}, {resultset 5, ao_Arg3} ) }  
    ```  
  
 Убедитесь, что приложения будут получать все наборы результатов с помощью API [S'LMoreResults.](../../odbc/microsoft/level-2-api-functions-odbc-driver-for-oracle.md) Для получения дополнительной информации, обратитесь к *справке программиста ODBC*.  
  
> [!NOTE]  
>  В ODBC Driver для версии Oracle 2.0 функции Oracle, возвращающие массивы PL/S'L, не могут быть использованы для возврата наборов результатов.
