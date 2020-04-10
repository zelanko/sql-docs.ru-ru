---
title: Метод setNull (java.lang.String, int, java.lang.String) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.setNull (java.lang.String, int, java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 16ff77f9-7928-415c-abf6-97ed59e3e396
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 377434a126d512b4d2b61bcdb1f9478605b6e943
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80913685"
---
# <a name="setnull-method-javalangstring-int-javalangstring"></a>Метод setNull (java.lang.String, int, java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Устанавливает указанный параметр в значение NULL по заданному имени и типу параметра.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setNull(java.lang.String sCol,  
                    int nType,  
                    java.lang.String sTypeName)  
```  
  
#### <a name="parameters"></a>Параметры  
 *sCol*  
  
 Значение **String**, содержащее имя параметра.  
  
 *nType*  
  
 Код типа JDBC, определенный в java.sql.Types.  
  
 *sTypeName*  
  
 Значение **String**, которое указывает полное имя задаваемого параметра.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод setNull определен с помощью метода setNull в интерфейсе java.sql.CallableStatement.  
  
## <a name="see-also"></a>См. также:  
 [Метод setNul (SQLServerCallableStatement)](../../../connect/jdbc/reference/setnull-method-sqlservercallablestatement.md)   
 [Элементы SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Класс SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
