---
title: Метод setString (SQLServerCallableStatement) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.setString
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f38b97b5-d4f0-4f74-a33d-740241a85842
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b36100c0a2b87abad223c47fc4c81dd802c16cc7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47682612"
---
# <a name="setstring-method-sqlservercallablestatement"></a>Метод setString (SQLServerCallableStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Задает назначенному параметру указанное значение **String** Java.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setString(java.lang.String sCol,  
                      java.lang.String s)  
```  
  
#### <a name="parameters"></a>Параметры  
 *sCol*  
  
 Значение типа **String**, содержащее имя параметра.  
  
 *s*  
  
 Значение типа **String**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод setString указывается методом setString в интерфейсе java.sql.CallableStatement.  
  
 Преобразования строкового типа данных в двоичный тип выполняются только в том случае, когда драйверу [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] известно, что целевой объект имеет двоичный тип. В случаях, когда драйверу JDBC неизвестен базовый тип, он будет передавать литерал **String** и возвращать ошибку сервера, если сервер не может выполнить преобразование.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Класс SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
