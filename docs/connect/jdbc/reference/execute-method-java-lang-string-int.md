---
title: Метод Execute (java.lang.String, int[]) | Документация Майкрософт
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
manager: jroth
ms.openlocfilehash: d4ae744a27156a59c926f2181ca9aec1146e8cd7
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66801656"
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

*columnIndexes*

Массив значений типа **int**, указывающих индексы столбцов автоматически сформированных ключей, которые должны быть доступными.

## <a name="return-value"></a>Возвращаемое значение
Значение **true**, если первый результат является результирующим набором. В противном случае — **false**.
  
## <a name="exceptions"></a>Исключения
[SQLServerException](./sqlserverexception-class.md)

## <a name="remarks"></a>Remarks
Этот метод execute определен с помощью метода execute в интерфейсе java.sql.PreparedStatement.

## <a name="see-also"></a>См. также:

[Метод Execute &#40;SQLServerStatement&#41;](./execute-method-sqlserverstatement.md)

[Элементы SQLServerStatement](./sqlserverstatement-members.md)

[Класс SQLServerStatement](./sqlserverstatement-class.md)
