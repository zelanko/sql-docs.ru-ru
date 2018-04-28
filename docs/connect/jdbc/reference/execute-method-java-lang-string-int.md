---
title: Метод Execute (java.lang.String, int[]) | Документы Microsoft
ms.custom: ''
ms.date: 02/07/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
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
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 86e02aa3ec56deffefe81ad5ebe4d282ecd10d53
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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
*sql*

Объект **строка** , содержащий инструкции SQL.

*columnIndexes*

Массив **int**типом, которые указывают индексы столбца автоматически сформированных ключей, которые должны быть доступными.

## <a name="return-value"></a>Возвращаемое значение
**значение true,** Если первый результат является результирующим набором. В противном случае — **false**.
  
## <a name="exceptions"></a>Исключения
[SQLServerException](./sqlserverexception-class.md)

## <a name="remarks"></a>Замечания
Этот метод execute указывается с помощью метода execute в интерфейсе java.sql.Statement.

## <a name="see-also"></a>См. также

[Метод Execute &#40;SQLServerStatement&#41;](./execute-method-sqlserverstatement.md)

[Члены SQLServerStatement](./sqlserverstatement-members.md)

[Класс SQLServerStatement](./sqlserverstatement-class.md)
