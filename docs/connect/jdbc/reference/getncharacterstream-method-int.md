---
title: Метод getNCharacterStream (int) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 6ae704f5-823c-4dfe-8c08-07b547c61a3c
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 28407a3328a1f92045cdb735e43136ad88da13fc
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="getncharacterstream-method-int"></a>Метод getNCharacterStream (int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Получает значение указанного параметра, как объект чтения по заданному индексу параметра.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final java.io.Reader getNCharacterStream(int parameterIndex)  
```  
  
#### <a name="parameters"></a>Параметры  
 *parameterIndex*  
  
 **Int** , указывающее индекс параметра.  
  
## <a name="return-value"></a>Возвращаемое значение  
 AReaderobject.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод следует использовать при доступе к **NCHAR**, **NVARCHAR** и **LONGNVARCHAR** параметров.  
  
 Этот метод getNCharacterStream указывается с помощью метода getNCharacterStream в интерфейсе java.sql.CallableStatement.  
  
## <a name="see-also"></a>См. также  
 [Метод getNCharacterStream &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/getncharacterstream-method-sqlservercallablestatement.md)   
 [Элементы SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)  
  
  
