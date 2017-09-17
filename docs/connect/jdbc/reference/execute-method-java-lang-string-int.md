---
title: "Метод Execute (java.lang.String, int[]) | Документы Microsoft"
ms.custom: 
ms.date: 02/07/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerStatement.execute (javal.lang.String.int[])
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: dc73d1c3-e756-43af-b1fc-ac438cbd0965
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 50cb9686b883ac0a4d682e7ea28f1dba40257c7e
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="execute-method-javalangstring-int"></a>Метод execute (java.lang.String, int[])

  Выполняет заданную инструкцию SQL, которая может вернуть несколько результатов и уведомляет [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion-md.md)] что автоматически сформированные ключи, отмеченные в заданном массиве должны быть доступны для загрузки.

## <a name="syntax"></a>Синтаксис

```Java
public final boolean execute(
    java.lang.String sql,
    int[] columnIndexes)
```

#### <a name="parameters"></a>Параметры
*SQL*

Объект **строка** , содержащий инструкции SQL.

*columnIndexes*

Массив **int**типом, которые указывают индексы столбца автоматически сформированных ключей, которые должны быть доступными.

## <a name="return-value"></a>Возвращаемое значение
**значение true,** Если первый результат является результирующим набором. В противном случае — **false**.
  
## <a name="exceptions"></a>Исключения
[SQLServerException](./sqlserverexception-class.md)

## <a name="remarks"></a>Замечания
Этот метод execute указывается с помощью метода execute в интерфейсе java.sql.Statement.

## <a name="see-also"></a>См. также:

[выполнение метода &#40; SQLServerStatement &#41;](./execute-method-sqlserverstatement.md)

[Члены SQLServerStatement](./sqlserverstatement-members.md)

[Класс SQLServerStatement](./sqlserverstatement-class.md)

