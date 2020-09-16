---
description: Метод getLoginTimeout (SQLServerDataSource)
title: Метод getLoginTimeout (SQLServerDataSource) | Документация Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d1a868a7fc9f562496037dd4280de91aac28b335
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88435736"
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
  
 Этот метод getLoginTimeout задается с помощью метода getLoginTimeout в интерфейсе javax.sql.DataSource.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
