---
title: Класс SQLServerCallableStatement | Документация Майкрософт
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
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "67971912"
---
# <a name="sqlservercallablestatement-class"></a>Класс SQLServerCallableStatement
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Позволяет указать имя вызываемой хранимой процедуры с входными и выходными параметрами. Этот класс также дает возможность получить значение состояния возврата с помощью синтаксиса ? синтаксис = call( ?, ..).  
  
 **Пакет:** com.microsoft.sqlserver.jdbc  
  
 **Реализует:** [ISQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
 **Расширяет:** [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final class SQLServerCallableStatement  
```  
  
## <a name="remarks"></a>Remarks  
 SQLServerCallableStatement позволяет указать имя вызываемой хранимой процедуры с входными и выходными параметрами. Кроме того, SQLServerCallableStatement позволяет получить значение состояния возврата с помощью синтаксиса `? = call( ?, ..)`.  
  
 Этот класс поддерживает распаковку в класс SQLServerCallableStatement, интерфейсы ISQLServerCallableStatement и java.sql.CallableStatement, и в любые другие классы и интерфейсы, для которых SQLServerPreparedStatement поддерживает распаковку. Дополнительные сведения см. в статье об [интерфейсах и программах-оболочках](../../../connect/jdbc/wrappers-and-interfaces.md).  
  
 Если вызван один из методов задания значений SQLServerCallableStatement с определенным типом, но этот тип конфликтует с указанным в [registerOutParameter](../../../connect/jdbc/reference/registeroutparameter-method-sqlservercallablestatement.md) типом, то используется тип, который был указан в последнем из методов задания значений SQLServerCallableStatement. Однако это может вызвать ошибки несовместимости преобразования типов данных. Если метод установки SQLServerCallableStatement не вызывается, то используется тип, заданный в первом вызове [registerOutParameter](../../../connect/jdbc/reference/registeroutparameter-method-sqlservercallablestatement.md).  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] JDBC Driver 3.0 соответствует рекомендации JDBC 4.0, согласно которой извлечение результирующего набора и счетчиков обновления происходит до извлечения параметров OUT. Если параметры OUT извлекаются до полной обработки результирующего набора и счетчиков обновлений, то любые, еще не обработанные результирующие наборы и счетчики обновлений будут утеряны.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Справка по API драйвера JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
