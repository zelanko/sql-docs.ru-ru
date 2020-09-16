---
description: Метод getScale (SQLServerParameterMetaData)
title: Метод getScale (SQLServerParameterMetaData) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerParameterMetaData.getScale
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7b8d8d9c-74aa-4e6e-88f1-2fc5c74004ae
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 12e9cd3e599a016601f587125dbd76f70d21410b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88434686"
---
# <a name="getscale-method-sqlserverparametermetadata"></a>Метод getScale (SQLServerParameterMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает число цифр справа от десятичной запятой для указанного параметра.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public int getScale(int param)  
```  
  
#### <a name="parameters"></a>Параметры  
 *param*  
  
 Значение **int**, указывающее индекс параметра.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **int**, указывающее масштаб заданного параметра.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getScale указывается с помощью метода getScale в интерфейсе java.sql.ParameterMetaData.  
  
 Этот метод возвращает количество разрядов в столбце справа от десятичного разделителя. Для типов без десятичного разделителя этот метод возвращает значение 0.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerParameterMetaData](../../../connect/jdbc/reference/sqlserverparametermetadata-methods.md)   
 [Элементы SQLServerParameterMetaData](../../../connect/jdbc/reference/sqlserverparametermetadata-members.md)   
 [Класс SQLServerParameterMetaData Class](../../../connect/jdbc/reference/sqlserverparametermetadata-class.md)  
  
  
