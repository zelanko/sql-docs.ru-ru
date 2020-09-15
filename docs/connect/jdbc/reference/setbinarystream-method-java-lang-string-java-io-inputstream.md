---
description: Метод setBinaryStream (java.lang.String, java.io.InputStream)
title: Метод setBinaryStream для входного потока | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 339c8277-2d08-4094-9fa9-26c8ad3e7348
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ce6bfbecdd30409a7bb3b5fe4cf11ebd7039d149
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88432456"
---
# <a name="setbinarystream-method-javalangstring-javaioinputstream"></a>Метод setBinaryStream (java.lang.String, java.io.InputStream)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Устанавливает для указанного параметра указанное значение входного потока.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setBinaryStream(java.lang.String parameterName,  
                            java.io.InputStream x)  
```  
  
#### <a name="parameters"></a>Параметры  
 *parameterName*  
  
 Значение типа **String**, содержащее имя параметра.  
  
 *x*  
  
 Объект InputStream.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод setBinaryStream задается с помощью метода setBinaryStream в интерфейсе java.sql.CallableStatement.  
  
## <a name="see-also"></a>См. также:  
 [setBinaryStream &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/setbinarystream-sqlservercallablestatement.md)   
 [Члены SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)  
  
  
