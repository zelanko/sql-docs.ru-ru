---
description: Метод setNClob (int, java.sql.NClob)
title: Метод setNClob (int, java.sql.NClob) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 48c8aa2a-4185-4837-b592-830e60f8ca0b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 866c1ce436dfa271219caab2d8ed71a60bff16ed
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88431566"
---
# <a name="setnclob-method-int-javasqlnclob"></a>Метод setNClob (int, java.sql.NClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Задает назначенному параметру значение указанного объекта NClob.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final void setNClob(int parameterIndex,  
              java.sql.NClob value)  
```  
  
#### <a name="parameters"></a>Параметры  
 *parameterIndex*  
  
 Значение типа **int**, указывающее индекс параметра.  
  
 *value*  
  
 Объект NClob, указывающий значение параметра.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод setNClob определен с помощью метода setNClob в интерфейсе java.sql.PreparedStatement.  
  
## <a name="see-also"></a>См. также:  
 [Метод setNClob (SQLServerPreparedStatement)](../../../connect/jdbc/reference/setnclob-method-sqlserverpreparedstatement.md)   
 [Члены SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)  
  
  
