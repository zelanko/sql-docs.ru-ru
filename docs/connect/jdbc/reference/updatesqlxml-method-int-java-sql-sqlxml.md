---
title: Метод updateSQLXML (int, java.sql.SQLXML) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b5170751-fbe1-433b-96f5-4f237ba55f60
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ee90c33b2b546a3eaf48d52b7577200b7c23306b
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "67998277"
---
# <a name="updatesqlxml-method-int-javasqlsqlxml"></a>Метод updateSQLXML (int, java.sql.SQLXML)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Обновляет указанный столбец значением java.sql.SQLXML  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void updateSQLXML(int columnIndex,  
                         java.sql.SQLXML xmlObject)  
```  
  
#### <a name="parameters"></a>Параметры  
 *columnIndex*  
  
 Значение типа **int**, указывающее индекс столбца.  
  
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
  
  
