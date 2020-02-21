---
title: Метод getParameterMode (SQLServerParameterMetaData) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerParameterMetaData.getParameterMode
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: d93c9b70-18c2-44bb-a6de-70a7e940d806
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ac7f8ba3b20ba8678891aeb3b14555a1123f06d1
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "67980940"
---
# <a name="getparametermode-method-sqlserverparametermetadata"></a>Метод getParameterMode (SQLServerParameterMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает режим указанного параметра.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public int getParameterMode(int param)  
```  
  
#### <a name="parameters"></a>Параметры  
 *param*  
  
 Значение **int**, указывающее индекс параметра.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **int**, указывающее режим указанного параметра. Возможно одно из следующих значений:  
  
 ParameterMetaData.parameterModeIn  
  
 ParameterMetaData.parameterModeInOut  
  
 ParameterMetaData.parameterModeOut  
  
 ParameterMetaData.parameterModeUnknown  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getParameterMode задается с помощью метода getParameterMode в интерфейсе java.sql.ParameterMetaData.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerParameterMetaData](../../../connect/jdbc/reference/sqlserverparametermetadata-methods.md)   
 [Элементы SQLServerParameterMetaData](../../../connect/jdbc/reference/sqlserverparametermetadata-members.md)   
 [Класс SQLServerParameterMetaData](../../../connect/jdbc/reference/sqlserverparametermetadata-class.md)  
  
  
