---
title: Метод getHostNameInCertificate (SQLServerDataSource) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- getHostNameInCertificate Method (SQLServerDataSource)
apilocation:
- getHostNameInCertificate Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: 45ea04e2-9ea5-4171-9136-d09f8a95e128
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 67978d2597a5167d3930c85ee453dc6d985f021e
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "67982900"
---
# <a name="gethostnameincertificate-method-sqlserverdatasource"></a>Метод getHostNameInCertificate (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает имя узла, используемого при проверке SSL-сертификата SQL Server.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.lang.String getHostNameInCertificate()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **String**, содержащее имя узла, или значение NULL, если значение не задано.  
  
## <a name="remarks"></a>Remarks  
 Имя узла используется для проверки значения SSL-сертификата SQL Server, если уровень связи шифруется с помощью SSL.  
  
 Если имя узла не задано, метод [getHostNameInCertificate](../../../connect/jdbc/reference/gethostnameincertificate-method-sqlserverdatasource.md) возвращает значение NULL.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
