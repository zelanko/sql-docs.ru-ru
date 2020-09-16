---
description: Метод registerOutParameter (int, int)
title: Метод registerOutParameter (int, int) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.registerOutParameter (int, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 169229c7-b75d-498b-a5ac-df300424c909
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 35b62512eb3ad9585704fa6720402fb4b6c4807a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88432886"
---
# <a name="registeroutparameter-method-int-int"></a>Метод registerOutParameter (int, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Регистрирует параметр OUT с указанным порядковым номером для заданного типа JDBC.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void registerOutParameter(int index,  
                                 int sqlType)  
```  
  
#### <a name="parameters"></a>Параметры  
 *index*  
  
 Значение типа **int**, указывающее порядковый номер параметра.  
  
 *sqlType*  
  
 Код типа JDBC, определенный в java.sql.Types.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод registerOutParameter задается с помощью метода registerOutParameter в интерфейсе java.sql.CallableStatement.  
  
 Начиная с версии [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] JDBC Driver 3.0, если параметр *sqlType* имеет тип java.sql.Types.TIME, то на работу этого метода влияет свойство подключения **sendTimeAsDatetime** ([Настройка свойств подключения](../../../connect/jdbc/setting-the-connection-properties.md)) и [SQLServerDataSourcTe.setSendTimeAsDatetime](../../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md).  
  
 Дополнительные сведения см. в статье [Настройка способа отправки значений java.sql.Time на сервер](../../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md).  
  
## <a name="see-also"></a>См. также:  
 [Метод registerOutParameter (SQLServerCallableStatement)](../../../connect/jdbc/reference/registeroutparameter-method-sqlservercallablestatement.md)   
 [Элементы SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Класс SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
