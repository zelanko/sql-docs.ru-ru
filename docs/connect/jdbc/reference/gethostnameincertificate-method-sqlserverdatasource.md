---
title: "Метод getHostNameInCertificate (SQLServerDataSource) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: getHostNameInCertificate Method (SQLServerDataSource)
apilocation: getHostNameInCertificate Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: 45ea04e2-9ea5-4171-9136-d09f8a95e128
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1fca55d9ba571f8c54a3efd766f4b02a72da3295
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="gethostnameincertificate-method-sqlserverdatasource"></a>Метод getHostNameInCertificate (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает имя узла, используемого при проверке SSL-сертификата SQL Server.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.lang.String getHostNameInCertificate()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект **строка** , содержащий узел имя или значение null, если значение не задано.  
  
## <a name="remarks"></a>Замечания  
 Имя узла используется для проверки значения SSL-сертификата SQL Server, если уровень связи шифруется с помощью SSL.  
  
 Если не указано имя узла, [getHostNameInCertificate](../../../connect/jdbc/reference/gethostnameincertificate-method-sqlserverdatasource.md) метод возвращает значение null.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
