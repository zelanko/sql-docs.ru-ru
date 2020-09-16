---
description: Метод setAsciiStream (int, java.io.InputStream)
title: Метод setAsciiStream (int, java.io.InputStream) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 02c2443d-44e1-4f16-a0d5-08d197838214
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 67a03bb83327d165591244c2301829fde30322f5
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88432616"
---
# <a name="setasciistream-method-int-javaioinputstream"></a>Метод setAsciiStream (int, java.io.InputStream)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Задает номер назначенного параметра для указанного объекта java.io.InputStream.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final void setAsciiStream(int parameterIndex,  
                                 java.io.InputStream x)  
```  
  
#### <a name="parameters"></a>Параметры  
 *parameterIndex*  
  
 Значение **int**, определяющее номер параметра.  
  
 *x*  
  
 Объект java.io.InputStream.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод setAsciiStream задается с помощью метода setAsciiStream в интерфейсе java.sql.PreparedStatement.  
  
## <a name="see-also"></a>См. также:  
 [Метод setAsciiStream (SQLServerPreparedStatement)](../../../connect/jdbc/reference/setasciistream-method-sqlserverpreparedstatement.md)   
 [Члены SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)  
  
  
