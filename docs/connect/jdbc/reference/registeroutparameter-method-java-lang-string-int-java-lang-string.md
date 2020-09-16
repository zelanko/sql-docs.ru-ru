---
description: Метод registerOutParameter (java.lang.String, int, java.lang.String)
title: Метод registerOutParameter для типа и имени | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.registerOutParameter
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f962c912-2475-4e1f-a384-579be2d17f37
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0fab9ba4e979780fedfb676fd779f8ed83da7566
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88432806"
---
# <a name="registeroutparameter-method-javalangstring-int-javalangstring"></a>Метод registerOutParameter (java.lang.String, int, java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Регистрирует параметр OUT с указанным именем для заданного типа и имени типа JDBC.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void registerOutParameter(java.lang.String s,  
                                 int n,  
                                 java.lang.String s1)  
```  
  
#### <a name="parameters"></a>Параметры  
 *s*  
  
 Значение типа **String**, содержащее имя параметра.  
  
 *n*  
  
 Код типа JDBC, определенный в java.sql.Types.  
  
 *s1*  
  
 Значение типа **String**, содержащее полное имя типа SQL.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод registerOutParameter задается с помощью метода registerOutParameter в интерфейсе java.sql.CallableStatement.  
  
## <a name="see-also"></a>См. также:  
 [Метод registerOutParameter (SQLServerCallableStatement)](../../../connect/jdbc/reference/registeroutparameter-method-sqlservercallablestatement.md)   
 [Элементы SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Класс SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
