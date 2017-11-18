---
title: "Метод setLastUpdateCount (SQLServerDataSource) | Документы Microsoft"
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
- SQLServerDataSource.setLastUpdateCount
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 5487631a-1107-4169-84ca-b77fd09bea66
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: caa3caa684088a38b732dddae8b17b7c88cf76bb
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="setlastupdatecount-method-sqlserverdatasource"></a>Метод setLastUpdateCount (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Наборы **логическое** значение, указывающее, включено ли свойство lastUpdateCount.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setLastUpdateCount(boolean lastUpdateCount)  
```  
  
#### <a name="parameters"></a>Параметры  
 *lastUpdateCount*  
  
 **значение true,** Если включено свойство lastUpdateCount. В противном случае — **false**.  
  
## <a name="remarks"></a>Замечания  
 Если свойство lastUpdateCount имеет значение **true**, [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] вернет только последний счетчик обновления из инструкции SQL, переданной серверу. Если свойство lastUpdateCount имеет значение **false**, драйвер вернет все счетчики обновлений, в том числе те, которые возвращены всеми сработавшими триггерами. Если свойство lastUpdateCount не задано, [getLastUpdateCount](../../../connect/jdbc/reference/getlastupdatecount-method-sqlserverdatasource.md) метод возвращает значение по умолчанию **true**.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  

