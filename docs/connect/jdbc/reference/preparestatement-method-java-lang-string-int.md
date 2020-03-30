---
title: Метод prepareStatement (java.lang.String) | Документация Майкрософт
ms.custom: ''
ms.date: 02/07/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.prepareStatement (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: e825765c-eb55-4800-951b-f3495da36641
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0c91b965498c0b617a02c7707e369a2ba61c0065
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "67976154"
---
# <a name="preparestatement-method-javalangstring"></a>Метод prepareStatement (java.lang.String)

Создает объект [SQLServerPreparedStatement](./sqlserverpreparedstatement-class.md) для отправки в базу данных параметризованных инструкций SQL.

## <a name="syntax"></a>Синтаксис

```
public java.sql.PreparedStatement prepareStatement(java.lang.String sql)
```

#### <a name="parameters"></a>Параметры
*sql*

Значение **String**, содержащее инструкцию SQL.

## <a name="return-value"></a>Возвращаемое значение
Объект PreparedStatement.

## <a name="exceptions"></a>Исключения  
[SQLServerException](./sqlserverexception-class.md)

## <a name="remarks"></a>Remarks
Этот метод prepareStatement определяется методом prepareStatement в интерфейсе java.sql.Connection.

## <a name="see-also"></a>См. также:

[Метод prepareStatement (SQLServerConnection)](./preparestatement-method-sqlserverconnection.md)

[Элементы SQLServerConnection](./sqlserverconnection-members.md)

[Класс SQLServerConnection](./sqlserverconnection-class.md)
