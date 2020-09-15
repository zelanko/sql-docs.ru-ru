---
description: Метод updateSQLXML (java.lang.String, java.sql.SQLXML)
title: Метод updateSQLXML (java.lang.String, java.sql.SQLXML) | Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 60021881-ef83-499b-9977-e20ff23c1312
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 80d597d42f17a6a08fc2d9f134f799c38ad04e8a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88431226"
---
# <a name="updatesqlxml-method-javalangstring-javasqlsqlxml"></a>Метод updateSQLXML (java.lang.String, java.sql.SQLXML)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Обновляет указанный столбец значением java.sql.SQLXML.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void updateSQLXML(java.lang.String columnLabel,  
                         java.sql.SQLXML xmlObject)  
```  
  
#### <a name="parameters"></a>Параметры  
 *columnLabel*  
  
 Значение **String**, которое указывает метку столбца.  
  
 *xmlObject*  
  
 Объект SQLXML.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод updateSQLXML задается с помощью метода updateSQLXML в интерфейсе java.sql.ResultSet.  
  
## <a name="see-also"></a>См. также:  
 [Метод updateSQLXML &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatesqlxml-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
