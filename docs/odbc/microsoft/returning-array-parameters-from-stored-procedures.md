---
description: Возврат параметров массива из хранимых процедур
title: Возврат параметров массива из хранимых процедур | Документация Майкрософт
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
ms.openlocfilehash: a6b18921e027e16f322c47da9757ef9c8ee7f1aa
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88449286"
---
# <a name="returning-array-parameters-from-stored-procedures"></a>Возврат параметров массива из хранимых процедур
> [!IMPORTANT]  
>  Эта функция будет удалена в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставляемый Oracle.  
  
 В Oracle 7,3 нет способа получить доступ к типу записи PL/SQL, за исключением программы PL/SQL. Если упакованная процедура или функция имеет формальный аргумент, определенный как тип записи PL/SQL, то невозможно привязать этот формальный аргумент в качестве параметра. Используйте тип таблицы PL/SQL в драйвере Microsoft ODBC для Oracle для вызова параметров массива из процедур, содержащих правильные escape-последовательности.  
  
 Чтобы вызвать процедуру, используйте следующий синтаксис:  
  
```  
{call  <package-name>.<proc-or-func>;  
(..., {resultset <max-records-requested> ,<formal-array-param_1>,;  
 <formal-array-param_2>,...,<formal-array-param_n> }, ... ) }  
```  
  
> [!NOTE]  
>  \<max-records-requested>Параметр должен быть больше или равен числу строк в результирующем наборе. В противном случае Oracle возвращает ошибку, которая передается пользователю драйвером.  
>   
>  Записи PL/SQL нельзя использовать в качестве параметров массива. Каждый параметр массива может представлять только один столбец таблицы базы данных.  
  
 В следующем примере определяется пакет, содержащий две процедуры, которые возвращают различные результирующие наборы, а затем предоставляет два способа возврата результирующих наборов из пакета.  
  
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
  
#### <a name="to-invoke-procedure-proc1"></a>Вызов процедуры PROC1  
  
1.  Возвращает все столбцы в одном результирующем наборе:  
  
    ```  
    {call SimplePackage.Proc1( {resultset  3, o_id , ao_course, ao_dept  } ) }  
    ```  
  
2.  Возврат каждого столбца в виде одного результирующего набора:  
  
    ```  
    {call SimplePackage.Proc1( {resultset 3, o_id},  {resultset 3, ao_course}, {resultset 3, ao_dept} ) }  
    ```  
  
     Это возвращает три результирующих набора, по одному для каждого столбца.  
  
#### <a name="to-invoke-procedure-proc2"></a>Вызов процедуры PROC2  
  
1.  Возвращает все столбцы в одном результирующем наборе:  
  
    ```  
    {call SimplePackage.Proc2( 5 , {resultset  5, ao_Arg2, ao_Arg3} ) }  
    ```  
  
2.  Возврат каждого столбца в виде одного результирующего набора:  
  
    ```  
    {call SimplePackage.Proc2( 5 , {resultset 5, ao_Arg2}, {resultset 5, ao_Arg3} ) }  
    ```  
  
 Убедитесь, что приложения получают все результирующие наборы с помощью API [SQLMoreResults](../../odbc/microsoft/level-2-api-functions-odbc-driver-for-oracle.md) . Дополнительные сведения см. в *справочнике программиста по ODBC*.  
  
> [!NOTE]  
>  В драйвере ODBC для Oracle версии 2,0 функции Oracle, возвращающие массивы PL/SQL, нельзя использовать для возвращения результирующих наборов.
