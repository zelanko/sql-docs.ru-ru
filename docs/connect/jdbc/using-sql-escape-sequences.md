---
title: С помощью Escape-последовательностей SQL | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 00f9e25a-088e-4ac6-aa75-43eacace8f03
caps.latest.revision: 25
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 72c7987e639a1902cb4271d91e255da5e5eb5377
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="using-sql-escape-sequences"></a>Использование escape-последовательностей SQL
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] Поддерживает использование escape-последовательностей SQL, в соответствии с определением API-интерфейса JDBC. Escape-последовательности используются в инструкции SQL для передачи драйверу сведений о том, что экранированные части SQL-строки должны обрабатываться иначе. При обработке драйвером JDBC части escape-последовательности SQL-строки выполняется преобразование этой части строки в SQL-код, распознаваемый SQL Server.  
  
 Существует пять типов escape-последовательностей, требуемых API JDBC, и все они поддерживаются драйвером JDBC:  
  
-   Литералы-шаблоны LIKE  
  
-   Обработка функций  
  
-   Литералы даты и времени  
  
-   Вызовы хранимых процедур  
  
-   Внешние соединения  
  
-   Escape-синтаксис LIMIT  
  
 Драйвер JDBC использует следующий синтаксис escape-последовательности:  
  
 `{keyword ...parameters...}`  
  
> [!NOTE]  
>  Для драйвера JDBC всегда включена обработка escape-последовательностей SQL.  
  
 В следующих разделах описывается пять типов escape-последовательностей и способы их поддержки драйвером JDBC.  
  
## <a name="like-wildcard-literals"></a>Литералы-шаблоны LIKE  
 Драйвер JDBC поддерживает `{escape 'escape character'}` синтаксис для использования шаблонов предложения LIKE в качестве литералов. Например, в следующем коде возвращаются значения col3, для которых значение col2 начинается с символа подчеркивания (и не используется как шаблон).  
  
```  
ResultSet rst = stmt.executeQuery("SELECT col3 FROM test1 WHERE col2   
LIKE '\\_%' {escape '\\'}");  
```  
  
> [!NOTE]  
>  Escape-последовательность должна быть в конце инструкции SQL. При наличии в командной строке нескольких инструкций SQL escape-последовательность должна быть в конце каждой соответствующей инструкции SQL.  
  
## <a name="function-handling"></a>Обработка функций  
 Драйвер JDBC поддерживает использование escape-последовательностей функций в инструкциях SQL со следующим синтаксисом:  
  
```  
{fn functionName}  
```  
  
 где `functionName` — это функция, поддерживаемых драйвером JDBC. Например:  
  
```  
SELECT {fn UCASE(Name)} FROM Employee  
```  
  
 В следующей таблице перечислены различные функции, поддерживаемые драйвером JDBC при использовании escape-последовательностей функций:  
  
|Строковые функции|Числовые функции|Функции Datetime|Системные функции|  
|----------------------|-----------------------|------------------------|----------------------|  
|ASCII<br /><br /> CHAR<br /><br /> CONCAT<br /><br /> DIFFERENCE<br /><br /> INSERT<br /><br /> LCASE<br /><br /> LEFT<br /><br /> LENGTH<br /><br /> LOCATE<br /><br /> LTRIM<br /><br /> REPEAT<br /><br /> REPLACE<br /><br /> RIGHT<br /><br /> RTRIM<br /><br /> SOUNDEX<br /><br /> SPACE<br /><br /> SUBSTRING<br /><br /> UCASE|ABS<br /><br /> ACOS<br /><br /> ASIN<br /><br /> ATAN<br /><br /> ATAN2<br /><br /> CEILING<br /><br /> COS<br /><br /> COT<br /><br /> DEGREES<br /><br /> EXP<br /><br /> FLOOR<br /><br /> LOG<br /><br /> LOG10<br /><br /> MOD<br /><br /> PI<br /><br /> POWER<br /><br /> RADIANS<br /><br /> RAND<br /><br /> ROUND<br /><br /> SIGN<br /><br /> SIN<br /><br /> SQRT<br /><br /> TAN<br /><br /> TRUNCATE|CURDATE<br /><br /> CURTIME<br /><br /> DAYNAME<br /><br /> DAYOFMONTH<br /><br /> DAYOFWEEK<br /><br /> DAYOFYEAR<br /><br /> EXTRACT<br /><br /> HOUR<br /><br /> MINUTE<br /><br /> MONTH<br /><br /> MONTHNAME<br /><br /> NOW<br /><br /> QUARTER<br /><br /> SECOND<br /><br /> TIMESTAMPADD<br /><br /> TIMESTAMPDIFF<br /><br /> WEEK<br /><br /> YEAR|DATABASE<br /><br /> IFNULL<br /><br /> Пользователь|  
  
> [!NOTE]  
>  Использование функции, не поддерживаемой базой данных, приведет к возникновению ошибки.  
  
## <a name="date-and-time-literals"></a>Литералы даты и времени  
 Ниже приводится синтаксис escape-последовательности для литералов даты, времени и отметок времени:  
  
```  
{literal-type 'value'}  
```  
  
 где `literal-type` является одним из следующих:  
  
|Тип литерала|Описание|Формат значения|  
|------------------|-----------------|------------------|  
|d|Дата|гггг-мм-дд|  
|t|Time|чч:мм:сс [1]|  
|ts|TimeStamp|гггг-мм-дд чч:мм:сс[.f...]|  
  
 Например:  
  
```  
UPDATE Orders SET OpenDate={d '2005-01-31'}   
WHERE OrderID=1025  
```  
  
## <a name="stored-procedure-calls"></a>Вызовы хранимых процедур  
 Драйвер JDBC поддерживает `{? = call proc_name(?,...)}` и `{call proc_name(?,...)}` escape-синтаксис для вызова хранимых процедур, в зависимости от того, требуется ли обработка возвращаемого параметра.  
  
 Процедура представляет собой исполняемый объект, который хранится в базе данных. Обычно процедурой является одна или несколько заранее скомпилированных инструкций SQL. Ниже приводится синтаксис escape-последовательности вызова хранимой процедуры:  
  
```  
{[?=]call procedure-name[([parameter][,[parameter]]...)]}  
```  
  
 где `procedure-name` указывает имя хранимой процедуры и `parameter` указывает параметр хранимой процедуры.  
  
 Дополнительные сведения об использовании `call` escape-последовательность с помощью хранимых процедур см. в разделе [с помощью инструкций с помощью хранимых процедур](../../connect/jdbc/using-statements-with-stored-procedures.md).  
  
## <a name="outer-joins"></a>Внешние соединения  
 Драйвер JDBC поддерживает синтаксис левого, правого и полного внешнего соединения SQL92. Ниже приводится синтаксис escape-последовательности для внешних соединений:  
  
```  
{oj outer-join}  
```  
  
 где внешнее соединение:  
  
```  
table-reference {LEFT | RIGHT | FULL} OUTER JOIN    
{table-reference | outer-join} ON search-condition  
```  
  
 где `table-reference` является именем таблицы и `search-condition` представляет собой условия соединения, которые вы хотите использовать для таблиц.  
  
 Например:  
  
```  
SELECT Customers.CustID, Customers.Name, Orders.OrderID, Orders.Status   
   FROM {oj Customers LEFT OUTER JOIN   
      Orders ON Customers.CustID=Orders.CustID}   
   WHERE Orders.Status='OPEN'  
```  
  
 Драйвер JDBC поддерживает следующие escape-последовательности внешнего соединения:  
  
-   Левые внешние соединения  
  
-   Правые внешние соединения  
  
-   Полные внешние соединения  
  
-   Вложенные внешние соединения  
  
## <a name="limit-escape-syntax"></a>Escape-синтаксис LIMIT  
  
> [!NOTE]  
>  Escape-синтаксис LIMIT поддерживается только драйвером Microsoft JDBC Driver 4.2 (или более поздней версии) для SQL Server при использовании JDBC 4.1 или более поздней версии.  
  
 Escape-синтаксис LIMIT выглядит следующим образом:  
  
```  
LIMIT <rows> [OFFSET <row offset>]  
```  
  
 Escape-синтаксис состоит из двух частей: \< *строк*> является обязательным и указывает количество возвращаемых строк. СМЕЩЕНИЕ и \< *смещение строки*> являются необязательными и укажите число строк необходимо пропустить перед началом возврата строк. Драйвер JDBC поддерживает только обязательную часть, преобразуя запрос для использования TOP вместо LIMIT. SQL Server не поддерживает предложение LIMIT. **Драйвер JDBC не поддерживает необязательный \<смещение строки > и драйвер вызовет исключение, если он используется**.  
  
## <a name="see-also"></a>См. также  
 [Использование инструкций с драйвером JDBC](../../connect/jdbc/using-statements-with-the-jdbc-driver.md)  
  
  
