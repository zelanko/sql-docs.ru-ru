---
title: Метод executeUpdate | Документация Майкрософт
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
ms.openlocfilehash: 04b3bdcd2b495513500d07583fadc910fe9c13a9
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "67954685"
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
Этот метод executeUpdate определен с помощью метода executeUpdate в интерфейсе java.sql.PreparedStatement.

Вызов этого метода приводит к исключению, поскольку инструкция SQL для объекта SQLServerPreparedStatement определена при создании объекта.

## <a name="see-also"></a>См. также:

[Метод executeUpdate (SQLServerPreparedStatement)](./executeupdate-method-sqlserverpreparedstatement.md)

[Элементы SQLServerPreparedStatement](./sqlserverpreparedstatement-members.md)

[Класс SQLServerPreparedStatement](./sqlserverpreparedstatement-class.md)
