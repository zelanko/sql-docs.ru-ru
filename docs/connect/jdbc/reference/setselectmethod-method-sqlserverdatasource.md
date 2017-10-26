---
title: "Метод setSelectMethod (SQLServerDataSource) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerDataSource.setSelectMethod
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7934276d-5ac9-4cbc-a2a0-2c65c93733ac
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 76ae74c63ac8cf87d0d7fb58f22f8cd1882d5208
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="setselectmethod-method-sqlserverdatasource"></a>Метод setSelectMethod (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Задает тип курсора по умолчанию, который используется для всех результирующих наборов, созданных с помощью этого [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setSelectMethod(java.lang.String selectMethod)  
```  
  
#### <a name="parameters"></a>Параметры  
 *метод selectMethod*  
  
 Объект **строка** значение, содержащее тип курсора по умолчанию.  
  
## <a name="remarks"></a>Замечания  
 Свойство selectMethod содержит тип курсора по умолчанию, который используется для результирующего набора. Это свойство полезно при работе с крупными результирующими наборами, когда не нужно сохранять результирующий набор целиком в памяти клиента. Если установить это свойство в значение cursor, то можно создать серверный курсор, который будет получать данные меньшими фрагментами. Если свойство selectMethod не задано, [getSelectMethod](../../../connect/jdbc/reference/getselectmethod-method-sqlserverdatasource.md) возвращает значение «direct» по умолчанию.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  

