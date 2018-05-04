---
title: Метод setString (SQLServerCallableStatement) | Документы Microsoft
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
- SQLServerCallableStatement.setString
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f38b97b5-d4f0-4f74-a33d-740241a85842
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 79ec2916b4611bf83ffe9ec52967b6409e8c84da
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="setstring-method-sqlservercallablestatement"></a>Метод setString (SQLServerCallableStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Устанавливает указанный параметр для заданного Java **строка** значение.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setString(java.lang.String sCol,  
                      java.lang.String s)  
```  
  
#### <a name="parameters"></a>Параметры  
 *sCol*  
  
 Объект **строка** , содержащее имя параметра.  
  
 *S*  
  
 Объект **строка** значение.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод setString задается с помощью метода setString в интерфейсе java.sql.CallableStatement.  
  
 Двоичный преобразования строковых значений в выполняются только если [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] знает объект назначения имеет двоичный тип. В случаях, когда драйвер JDBC неизвестен базовый тип, то он передает **строка** литерал и возвращать ошибку сервера, если сервер не может выполнить преобразование.  
  
## <a name="see-also"></a>См. также  
 [Члены SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Класс SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
