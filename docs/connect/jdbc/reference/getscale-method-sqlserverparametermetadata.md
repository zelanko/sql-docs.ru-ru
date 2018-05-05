---
title: Метод getScale (SQLServerParameterMetaData) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerParameterMetaData.getScale
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7b8d8d9c-74aa-4e6e-88f1-2fc5c74004ae
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e77c6dcfd46b6fbb522312738bd24c9f4ac94fe0
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
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
  
 **Int** , указывающее индекс параметра.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В **int** , указывающее масштаб заданного параметра.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод getScale указывается с помощью метода getScale в интерфейсе java.sql.ParameterMetaData.  
  
 Этот метод возвращает количество разрядов в столбце справа от десятичного разделителя. Для типов без десятичного разделителя этот метод возвращает значение 0.  
  
## <a name="see-also"></a>См. также  
 [Методы SQLServerParameterMetaData](../../../connect/jdbc/reference/sqlserverparametermetadata-methods.md)   
 [Элементы SQLServerParameterMetaData](../../../connect/jdbc/reference/sqlserverparametermetadata-members.md)   
 [Класс SQLServerParameterMetaData](../../../connect/jdbc/reference/sqlserverparametermetadata-class.md)  
  
  
