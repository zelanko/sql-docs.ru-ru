---
title: Возврат массива параметров с хранимыми процедурами | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- stored procedures [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], stored procedures
ms.assetid: 2018069b-da5d-4cee-a971-991897d4f7b5
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6f67a9044dcd95b2b652c310e066843b7aa5d1ab
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32903740"
---
# <a name="returning-array-parameters-from-stored-procedures"></a>Возврат массива параметров из хранимых процедур
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставляемого корпорацией Oracle.  
  
 В Oracle 7.3 нет возможности получить доступ к типом записи PL/SQL, за исключением программы PL/SQL. Если упакованных процедура или функция имеет формальный аргумент определен как тип записи PL/SQL, не позволяет привязать этого формального аргумента в качестве параметра. Тип таблицы PL/SQL в драйвер ODBC для Oracle можно используйте для вызова параметров массива из процедур, содержащих правильный escape-последовательности.  
  
 Чтобы вызвать процедуру, используйте следующий синтаксис:  
  
```  
{call  <package-name>.<proc-or-func>;  
(..., {resultset <max-records-requested> ,<formal-array-param_1>,;  
 <formal-array-param_2>,...,<formal-array-param_n> }, ... ) }  
```  
  
> [!NOTE]  
>  \<Max записей запрошенный > параметр должен быть больше или равно числу строк в результирующем наборе. В противном случае Oracle возвращает ошибку, которая передается пользователю драйвером.  
>   
>  Записи PL/SQL не может использоваться в качестве массива параметров. Каждый параметр массива может быть представлен только один столбец таблицы базы данных.  
  
 Следующий пример определяет пакет, содержащий две процедуры, возвращающие различных результирующих наборов, а затем предоставляет два способа возврата результирующих наборов из пакета.  
  
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
  
#### <a name="to-invoke-procedure-proc1"></a>Для вызова процедуры PROC1  
  
1.  Возвращает все столбцы в единый результирующий набор:  
  
    ```  
    {call SimplePackage.Proc1( {resultset  3, o_id , ao_course, ao_dept  } ) }  
    ```  
  
2.  Возврат каждого столбца в виде единого результирующего набора:  
  
    ```  
    {call SimplePackage.Proc1( {resultset 3, o_id},  {resultset 3, ao_course}, {resultset 3, ao_dept} ) }  
    ```  
  
     Это возвращает три результирующих наборов, по одному для каждого столбца.  
  
#### <a name="to-invoke-procedure-proc2"></a>Для вызова процедуры PROC2  
  
1.  Возвращает все столбцы в единый результирующий набор:  
  
    ```  
    {call SimplePackage.Proc2( 5 , {resultset  5, ao_Arg2, ao_Arg3} ) }  
    ```  
  
2.  Возврат каждого столбца в виде единого результирующего набора:  
  
    ```  
    {call SimplePackage.Proc2( 5 , {resultset 5, ao_Arg2}, {resultset 5, ao_Arg3} ) }  
    ```  
  
 Убедитесь, что приложения извлечь все результирующие наборы с помощью [SQLMoreResults](../../odbc/microsoft/level-2-api-functions-odbc-driver-for-oracle.md) API. Дополнительные сведения см. в *справочнике программиста ODBC*.  
  
> [!NOTE]  
>  В драйвере ODBC для Oracle версии 2.0 Oracle функции, возвращающие массивы PL/SQL не может использоваться для возврата результирующих наборов.
