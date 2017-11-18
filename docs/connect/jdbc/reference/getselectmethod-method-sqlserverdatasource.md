---
title: "Метод getSelectMethod (SQLServerDataSource) | Документы Microsoft"
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
- SQLServerDataSource.getSelectMethod
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b6255d2e-0028-474a-afa8-553ef092243e
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: dae0422612846e25cb2d2a60273f753802df3da0
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="getselectmethod-method-sqlserverdatasource"></a>Метод getSelectMethod (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает тип курсора по умолчанию, используемый для всех результирующих наборов, созданных с помощью этого [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.lang.String getSelectMethod()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект **строка** значение, содержащее тип курсора по умолчанию.  
  
## <a name="remarks"></a>Замечания  
 Свойство selectMethod задает тип курсора по умолчанию, который используется для результирующего набора. Это свойство полезно при работе с крупными результирующими наборами, когда не нужно сохранять результирующий набор целиком в памяти клиента. Если установить это свойство в значение cursor, то можно создать серверный курсор, который будет получать данные меньшими фрагментами. Если свойство selectMethod не задано, метод getSelectMethod возвращает значение по умолчанию (direct).  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  

