---
title: Метод getParameterCount (SQLServerParameterMetaData) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerParameterMetaData.getParameterCount
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7dbbdacb-74ef-42e7-9bdc-a3229505dad8
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 74c2228b944dce2f9c59f4f8fcfc4bc0ac2e5753
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "67980989"
---
# <a name="getparametercount-method-sqlserverparametermetadata"></a>Метод getParameterCount (SQLServerParameterMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает число параметров в объекте [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md), для которого объект [SQLServerParameterMetaData](../../../connect/jdbc/reference/sqlserverparametermetadata-class.md) содержит данные.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public int getParameterCount()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **int**, указывающее количество параметров.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getParameterCount задается с помощью метода getParameterCount в интерфейсе java.sql.ParameterMetaData.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerParameterMetaData](../../../connect/jdbc/reference/sqlserverparametermetadata-methods.md)   
 [Элементы SQLServerParameterMetaData](../../../connect/jdbc/reference/sqlserverparametermetadata-members.md)   
 [Класс SQLServerParameterMetaData](../../../connect/jdbc/reference/sqlserverparametermetadata-class.md)  
  
  
