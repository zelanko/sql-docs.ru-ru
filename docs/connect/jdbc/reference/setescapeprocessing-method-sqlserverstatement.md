---
title: "Метод setEscapeProcessing (SQLServerStatement) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerStatement.setEscapeProcessing
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 6ac0682e-e04c-4fdb-893b-92408d42051e
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 5e7c53393acca2a1ad95d590ce28fbd7b943b534
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="setescapeprocessing-method-sqlserverstatement"></a>Метод setEscapeProcessing (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Задается режим обработки escape-последовательностей.  
  
> [!NOTE]  
>  Обработка escape [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] всегда включена. Если установить значение false в этом методе, обработка останется включенной.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final void setEscapeProcessing(boolean enable)  
```  
  
#### <a name="parameters"></a>Параметры  
 *включить*  
  
 **значение true,** Чтобы включить обработку escape-последовательностей. В противном случае — **false**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод setEscapeProcessing указывается с помощью метода setEscapeProcessing в интерфейсе java.sql.Statement.  
  
## <a name="see-also"></a>См. также:  
 [Члены SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Класс SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  

