---
description: Метод prepareStatement (java.lang.String)
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f9cec12d2443e84ef3334e19253a64ff60fea1c9
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88432866"
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
