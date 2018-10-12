---
title: Метод getLoginTimeout (SQLServerDataSource) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getLoginTimeout
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 316f067c-9e08-456a-af19-b80b0bbd4a5c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 26a7c8e0cc876c8d13e9beb621354cead2f6296c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47708582"
---
# <a name="getlogintimeout-method-sqlserverdatasource"></a>Метод getLoginTimeout (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает время в секундах, которое будет ждать объект [SQLServerDataSource Class](../../../connect/jdbc/reference/sqlserverdatasource-class.md) при попытке установить соединение.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public int getLoginTimeout()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **int**, представляющее число секунд ожидания.  
  
## <a name="remarks"></a>Remarks  
 Если приложение не указывает явно значение периода ожидания, этот метод возвращает значение по умолчанию 15 секунд.  
  
 Этот метод getLoginTimeout указывается с помощью метода getLoginTimeout в интерфейсе javax.sql.DataSource.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
