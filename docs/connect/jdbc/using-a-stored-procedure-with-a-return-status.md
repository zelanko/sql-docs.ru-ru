---
title: Использование хранимых процедур с состояниями возврата | Документы Майкрософт
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 4b126e95-8458-41d6-af37-fc6662859f19
author: MightyPen
ms.author: genemi
ms.openlocfilehash: eb5654563a0894abd497dfb0053b3e5667bf433d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67916513"
---
# <a name="using-a-stored-procedure-with-a-return-status"></a>Использование хранимых процедур с состояниями возврата

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Вызываемая хранимая процедура [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] — это процедура, которая возвращает параметр состояния или параметр результата. Обычно используется для указания успешного выполнения или ошибки хранимой процедуры. В драйвере [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] имеется класс [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md), который можно использовать для вызова этого типа хранимых процедур и обработки возвращаемых ими данных.

При вызове хранимой процедуры этого типа с помощью драйвера JDBC следует использовать escape-последовательность SQL `call` совместно с методом [prepareCall](../../connect/jdbc/reference/preparecall-method-sqlserverconnection.md) класса [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md). Ниже приводится синтаксис escape-последовательности `call` с возвращаемым параметром состояния:

`{[?=]call procedure-name[([parameter][,[parameter]]...)]}`

> [!NOTE]  
> Дополнительные сведения о escape-последовательностях SQL см. в разделе [использование escape](../../connect/jdbc/using-sql-escape-sequences.md)-последовательностей SQL.

При создании escape-последовательности `call` укажите возвращаемый параметр состояния с помощью символа "?" (символ вопросительного знака (?)). Этот символ выполняет роль заполнителя для значения параметра, которое будет возвращено из хранимой процедуры. Чтобы указать значение возвращаемого параметра состояния, необходимо задать тип данных параметра с помощью метода [registerOutParameter](../../connect/jdbc/reference/registeroutparameter-method-sqlservercallablestatement.md) класса SQLServerCallableStatement до выполнения хранимой процедуры.

> [!NOTE]  
> При использовании драйвера JDBC с базой данных SQL Server значение, указываемое для возвращаемого параметра состояния в методе registerOutParameter, всегда будет целым числом, которое можно задать с помощью типа данных java.sql.Types.INTEGER.

Кроме того, при передаче значения методу registerOutParameter для возвращаемого параметра состояния необходимо указать не только тип данных, который будет использоваться для параметра, но также порядковое размещение параметра в вызове хранимой процедуры. Порядковое местоположение возвращаемого параметра состояния всегда будет 1, поскольку этот параметр всегда является первым в вызове в хранимой процедуры. Хотя класс SQLServerCallableStatement обеспечивает поддержку использования имени параметра для указания определенного параметра, для возвращаемых параметров состояния можно использовать только номер порядкового местоположения.

Для примера создайте следующую хранимую процедуру в образце базы данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]:

```sql
CREATE PROCEDURE CheckContactCity  
   (@cityName CHAR(50))  
AS  
BEGIN  
   IF ((SELECT COUNT(*)  
   FROM Person.Address  
   WHERE City = @cityName) > 1)  
   RETURN 1  
ELSE  
   RETURN 0  
END  
```

Эта хранимая процедура возвращает значение состояния 1 или 0, в зависимости от того, включен ли город, указанный в параметре cityName, в таблицу Person.Address.

В приведенном ниже примере открытое подключение к образцу базы данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] передается в функцию, а метод [execute](../../connect/jdbc/reference/execute-method-sqlserverstatement.md) используется для вызова хранимой процедуры CheckContactCity.

[!code[JDBC#UsingSprocWithReturnStatus1](../../connect/jdbc/codesnippet/Java/using-a-stored-procedure_1_1.java)]

## <a name="see-also"></a>См. также:

[Использование инструкций с хранимыми процедурами](../../connect/jdbc/using-statements-with-stored-procedures.md)
