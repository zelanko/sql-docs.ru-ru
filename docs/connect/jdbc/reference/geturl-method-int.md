---
description: Метод getURL (int)
title: Метод getURL (int) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.getURL Ijnt)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 75d03ced-3614-4997-9abd-24642b1d1aae
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f21b85039805f6b636b79be05fa0eb7a4f105abb
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88433886"
---
# <a name="geturl-method-int"></a>Метод getURL (int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Извлекает значение назначенного параметра в виде объекта URL на языке программирования Java по заданному индексу параметра.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.net.URL getURL(int n)  
```  
  
#### <a name="parameters"></a>Параметры  
 *n*  
  
 Значение типа **int**, указывающее индекс параметра.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект URL.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getURL определен с помощью метода getURL в интерфейсе java.sql.CallableStatement.  
  
## <a name="see-also"></a>См. также:  
 [Метод getURL (SQLServerCallableStatement)](../../../connect/jdbc/reference/geturl-method-sqlservercallablestatement.md)   
 [Элементы SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Класс SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
