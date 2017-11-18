---
title: "Метод prepareStatement (java.lang.String) | Документы Microsoft"
ms.custom: 
ms.date: 02/07/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerConnection.prepareStatement (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: e825765c-eb55-4800-951b-f3495da36641
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c2452837aba5b8c5a146c12de838a3259f65be38
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="preparestatement-method-javalangstring"></a>Метод prepareStatement (java.lang.String)

Создает [SQLServerPreparedStatement](./sqlserverpreparedstatement-class.md) объект для отправки параметризованных инструкций SQL в базу данных.

## <a name="syntax"></a>Синтаксис

```
public java.sql.PreparedStatement prepareStatement(java.lang.String sql)
```

#### <a name="parameters"></a>Параметры
*SQL*

Объект **строка** содержащее инструкцию SQL.

## <a name="return-value"></a>Возвращаемое значение
Объект PreparedStatement.

## <a name="exceptions"></a>Исключения  
[SQLServerException](./sqlserverexception-class.md)

## <a name="remarks"></a>Замечания
Этот метод prepareStatement указывается с помощью метода prepareStatement в интерфейсе java.sql.Connection.

## <a name="see-also"></a>См. также:

[Метод prepareStatement &#40; SQLServerConnection &#41;](./preparestatement-method-sqlserverconnection.md)

[Элементы SQLServerConnection](./sqlserverconnection-members.md)

[Класс SQLServerConnection](./sqlserverconnection-class.md)

