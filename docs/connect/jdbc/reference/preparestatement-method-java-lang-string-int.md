---
title: Метод prepareStatement (java.lang.String) | Документы Microsoft
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
ms.topic: conceptual
apiname:
- SQLServerConnection.prepareStatement (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: e825765c-eb55-4800-951b-f3495da36641
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: afd095efadf10a6838fb5ba8f6abec6a6f9e0bb5
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="preparestatement-method-javalangstring"></a>Метод prepareStatement (java.lang.String)

Создает [SQLServerPreparedStatement](./sqlserverpreparedstatement-class.md) объект для отправки параметризованных инструкций SQL в базу данных.

## <a name="syntax"></a>Синтаксис

```
public java.sql.PreparedStatement prepareStatement(java.lang.String sql)
```

#### <a name="parameters"></a>Параметры
*sql*

Объект **строка** содержащее инструкцию SQL.

## <a name="return-value"></a>Возвращаемое значение
Объект PreparedStatement.

## <a name="exceptions"></a>Исключения  
[SQLServerException](./sqlserverexception-class.md)

## <a name="remarks"></a>Замечания
Этот метод prepareStatement указывается с помощью метода prepareStatement в интерфейсе java.sql.Connection.

## <a name="see-also"></a>См. также

[Метод prepareStatement &#40;SQLServerConnection&#41;](./preparestatement-method-sqlserverconnection.md)

[Элементы SQLServerConnection](./sqlserverconnection-members.md)

[Класс SQLServerConnection](./sqlserverconnection-class.md)
