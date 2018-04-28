---
title: Метод executeUpdate (java.lang.String) | Документы Microsoft
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
- SQLServerPreparedStatement.executeUpdate (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 91ecb1cd-001d-4ac9-9ae8-5db05c3c2959
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: aa8aef31d1df6798bc209fb1dbb95ef8c58cb3ce
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="executeupdate-method-javalangstring"></a>Метод executeUpdate (java.lang.String)

Выполняет заданную инструкцию SQL, которой может быть инструкция INSERT, UPDATE, MERGE или DELETE, либо инструкцию SQL, не возвращающую значения, например инструкцию SQL DDL.

## <a name="syntax"></a>Синтаксис

```
public final int executeUpdate(java.lang.String sql)
```

#### <a name="parameters"></a>Параметры
*sql*

Объект **строка** , содержащий инструкции SQL.

## <a name="return-value"></a>Возвращаемое значение
**Int** указывает число обработанных строк, либо значение 0 для инструкций DDL.

## <a name="exceptions"></a>Исключения
[SQLServerException](./sqlserverexception-class.md)

## <a name="remarks"></a>Замечания
Этот метод executeUpdate указывается с помощью метода executeUpdate в интерфейсе java.sql.PreparedStatement.

Вызов этого метода будет приведет к исключению, поскольку задан в инструкции SQL для объекта SQLServerPreparedStatement при создании объекта.

## <a name="see-also"></a>См. также

[Метод executeUpdate &#40;SQLServerPreparedStatement&#41;](./executeupdate-method-sqlserverpreparedstatement.md)

[Элементы SQLServerPreparedStatement](./sqlserverpreparedstatement-members.md)

[Класс SQLServerPreparedStatement](./sqlserverpreparedstatement-class.md)
