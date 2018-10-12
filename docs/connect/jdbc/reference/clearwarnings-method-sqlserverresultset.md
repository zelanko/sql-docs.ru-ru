---
title: Метод clearWarnings (SQLServerResultSet) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.clearWarnings
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f55af4b6-ae5c-41c9-8aa3-8313773f5443
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a2cdba3c27c440fbe69e499634a755586aac2058
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47733712"
---
# <a name="clearwarnings-method-sqlserverresultset"></a>Метод clearWarnings (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Удаляет все предупреждения, включенные в отчет для этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
> [!NOTE]  
>  В настоящее время этот метод не реализуется драйвером [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]. При вызове он всегда возвращает значение NULL.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void clearWarnings()  
```  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод clearWarnings указывается с помощью метода clearWarnings в интерфейсе java.sql.ResultSet.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
