---
title: Метод executeUpdate (java.lang.String, java.lang.String) | Документация Майкрософт
ms.custom: ''
ms.date: 02/07/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerPreparedStatement.executeUpdate (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 91ecb1cd-001d-4ac9-9ae8-5db05c3c2959
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 8c408098ebe1e9e732b171390eb1901f01014292
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66804146"
---
# <a name="executeupdate-method-javalangstring"></a>Метод executeUpdate (java.lang.String)

Выполняет заданную инструкцию SQL, которой может быть инструкция INSERT, UPDATE, MERGE или DELETE, либо инструкцию SQL, не возвращающую значения, например инструкцию SQL DDL.

## <a name="syntax"></a>Синтаксис

```
public final int executeUpdate(java.lang.String sql)
```

#### <a name="parameters"></a>Параметры
*sql*

Значение типа **String**, содержащее инструкцию SQL.

## <a name="return-value"></a>Возвращаемое значение
Значение типа **int**, указывающее либо число обработанных строк, либо значение 0 для инструкций языка DDL.

## <a name="exceptions"></a>Исключения
[SQLServerException](./sqlserverexception-class.md)

## <a name="remarks"></a>Remarks
Этот метод execute определен с помощью метода execute в интерфейсе java.sql.PreparedStatement.

Вызов этого метода приводит к исключению, поскольку инструкция SQL для объекта SQLServerPreparedStatement определена при создании объекта.

## <a name="see-also"></a>См. также:

[Метод executeUpdate (SQLServerPreparedStatement)](./executeupdate-method-sqlserverpreparedstatement.md)

[Элементы SQLServerPreparedStatement](./sqlserverpreparedstatement-members.md)

[Класс SQLServerPreparedStatement](./sqlserverpreparedstatement-class.md)
