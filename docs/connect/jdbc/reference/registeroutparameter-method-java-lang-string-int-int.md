---
title: Метод registerOutParameter для типа и масштаба | Документы Microsoft
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
apiname:
- SQLServerCallableStatement.registerOutParameter (java.lang.String, int, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 8bddc557-4526-4843-9804-05dc83c8832d
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0114197dc191b80637ed6a01c277d4a154764c92
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="registeroutparameter-method-javalangstring-int-int"></a>Метод registerOutParameter (java.lang.String, int, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Регистрирует параметр OUT с указанным именем для заданного типа и масштаба JDBC.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void registerOutParameter(java.lang.String s,  
                                 int n,  
                                 int n1)  
```  
  
#### <a name="parameters"></a>Параметры  
 *S*  
  
 Объект **строка** , содержащее имя параметра.  
  
 *SQLtype*  
  
 Код типа JDBC, определенный в java.sql.Types.  
  
 *масштаб*  
  
 **Int** указывает количество цифр, должен располагаться справа от десятичной запятой.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод registerOutParameter указывается с помощью метода registerOutParameter в интерфейсе java.sql.CallableStatement.  
  
## <a name="see-also"></a>См. также  
 [Метод registerOutParameter &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/registeroutparameter-method-sqlservercallablestatement.md)   
 [Члены SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Класс SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
