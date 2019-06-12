---
title: Метод getGeneratedKeys (SQLServerStatement) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.getGeneratedKeys
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: a3325950-0e81-4ae8-aa0c-e1f6d371adcd
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: e81fe589ed70f4d3f230713290f1d7f9b338ea67
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66774647"
---
# <a name="getgeneratedkeys-method-sqlserverstatement"></a>Метод getGeneratedKeys (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Извлекает все автоматически сформированные ключи, созданные в результате выполнения этого объекта [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final java.sql.ResultSet getGeneratedKeys()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект результирующего набора.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getGeneratedKeys указывается методом getGeneratedKeys в интерфейсе java.sql.Statement.  
  
 Дополнительные сведения об использовании этого метода см. в разделе [с помощью автоматически формируемых ключей](../../../connect/jdbc/using-auto-generated-keys.md).  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Класс SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
