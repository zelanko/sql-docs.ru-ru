---
title: Класс SQLServerCallableStatement | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 30710a63-c05d-47d9-9cf9-c087a1c76373
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 637b56c7f64d35501be0efef30e8f2a055b5be4b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67971912"
---
# <a name="sqlservercallablestatement-class"></a>Класс SQLServerCallableStatement
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Позволяет указать имя вызываемой хранимой процедуры с входными и выходными параметрами. Этот класс также дает возможность получить значение состояния возврата с помощью синтаксиса ? синтаксис = call( ?, ..).  
  
 **Пакет:** com.microsoft.sqlserver.jdbc  
  
 **Реализует**: [ISQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
 **Расширяет**: [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final class SQLServerCallableStatement  
```  
  
## <a name="remarks"></a>Remarks  
 SQLServerCallableStatement позволяет указать имя вызываемой хранимой процедуры с входными и выходными параметрами. SQLServerCallableStatement также дает возможность получить значение состояния возврата с помощью `? = call( ?, ..)` синтаксиса.  
  
 Этот класс поддерживает распаковку в класс SQLServerCallableStatement, интерфейс ISQLServerCallableStatement, Java. SQL. CallableStatement, а также классы и интерфейсы, поддерживаемые SQLServerPreparedStatement для распаковки. Дополнительные сведения см. в разделе [оболочки и интерфейсы](../../../connect/jdbc/wrappers-and-interfaces.md).  
  
 Если один из методов набора SQLServerCallableStatement вызывается для типа, если этот тип конфликтует с типом, указанным в [registerOutParameter](../../../connect/jdbc/reference/registeroutparameter-method-sqlservercallablestatement.md), используется тип, заданный последним методом set SQLServerCallableStatement. Однако это может вызвать ошибки несовместимости преобразования типов данных. Если метод установки SQLServerCallableStatement не вызывается, то используется тип, заданный в первом вызове [registerOutParameter](../../../connect/jdbc/reference/registeroutparameter-method-sqlservercallablestatement.md).  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] JDBC Driver 3.0 соответствует рекомендации JDBC 4.0, согласно которой извлечение результирующего набора и счетчиков обновления происходит до извлечения параметров OUT. Если параметры OUT извлекаются до полной обработки результирующего набора и счетчиков обновлений, то любые, еще не обработанные результирующие наборы и счетчики обновлений будут утеряны.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Справка по API драйвера JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
