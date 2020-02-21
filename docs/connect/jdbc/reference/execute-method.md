---
title: Метод execute () | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerPreparedStatement.execute ()
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: fa96d0f8-101b-422f-a767-405be9a5f74f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9f7e87040fa74954435ed52f9923568e8bfed3fd
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "67954929"
---
# <a name="execute-method-"></a>Метод execute ()
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Выполняет в этом объекте [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) инструкцию SQL любого типа.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean execute()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 **true**, если инструкция возвращает результирующий набор. **false**, если инструкция возвращает число обновлений или не имеет результата.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод execute определен с помощью метода execute в интерфейсе java.sql.PreparedStatement.  
  
## <a name="see-also"></a>См. также:  
 [Метод execute (SQLServerPreparedStatement)](../../../connect/jdbc/reference/execute-method-sqlserverpreparedstatement.md)   
 [Элементы SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [Класс SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
