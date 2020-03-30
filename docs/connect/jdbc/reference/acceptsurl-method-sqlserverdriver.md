---
title: Метод acceptsURL (SQLServerDriver) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDriver.acceptsURL
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: fc744566-7191-4b15-9f76-b4b8087fb14a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7c51da69e7218f91630543fe7bee5ec0d7fd6b0e
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "67956029"
---
# <a name="acceptsurl-method-sqlserverdriver"></a>Метод acceptsURL (SQLServerDriver)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Проверяет допустимость заданного URL-адреса.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean acceptsURL(java.lang.String url)  
```  
  
#### <a name="parameters"></a>Параметры  
 *url*  
  
 Значение типа **String**, содержащее URL-адрес, который используется для подключения к базе данных.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **true**, если заданный URL-адрес недопустим. В противном случае — **false**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод acceptsURL задается с помощью метода acceptsURL в интерфейсе java.sql.Driver.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerDriver](../../../connect/jdbc/reference/sqlserverdriver-methods.md)   
 [Элементы SQLServerDriver](../../../connect/jdbc/reference/sqlserverdriver-members.md)   
 [Класс SQLServerDriver](../../../connect/jdbc/reference/sqlserverdriver-class.md)  
  
  
