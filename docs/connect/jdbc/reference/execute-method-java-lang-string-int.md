---
title: Метод execute (java.lang.String, int[]) | Документация Майкрософт
ms.custom: ''
ms.date: 02/07/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.execute (javal.lang.String.int[])
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: dc73d1c3-e756-43af-b1fc-ac438cbd0965
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6e96e0c9c957522db6a766b3491d394b7337d7b6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67954984"
---
# <a name="execute-method-javalangstring-int"></a>Метод execute (java.lang.String, int[])

  Выполняет заданную инструкцию SQL, которая может вернуть несколько результатов, и уведомляет [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] о том, что автоматически сформированные ключи, отмеченные в указанном массиве, должны быть доступны для получения.

## <a name="syntax"></a>Синтаксис

```Java
public final boolean execute(
    java.lang.String sql,
    int[] columnIndexes)
```

#### <a name="parameters"></a>Параметры
*sql*

Значение типа **String**, содержащее инструкцию SQL.

*колумниндексес*

Массив значений типа **int**, указывающих индексы столбцов автоматически сформированных ключей, которые должны быть доступными.

## <a name="return-value"></a>Возвращаемое значение
Значение **true**, если первый результат является результирующим набором. В противном случае — **false**.
  
## <a name="exceptions"></a>Исключения
[SQLServerException](./sqlserverexception-class.md)

## <a name="remarks"></a>Remarks
Этот метод execute определен с помощью метода execute в интерфейсе java.sql.Statement.

## <a name="see-also"></a>См. также:

[Метод &#40;Execute SQLServerStatement&#41;](./execute-method-sqlserverstatement.md)

[Элементы SQLServerStatement](./sqlserverstatement-members.md)

[Класс SQLServerStatement](./sqlserverstatement-class.md)
