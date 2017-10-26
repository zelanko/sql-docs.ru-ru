---
title: "Метод getLastUpdateCount (SQLServerDataSource) | Документы Microsoft"
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
- SQLServerDataSource.getLastUpdateCount
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 4c4fbb24-0b02-42da-928c-a903bb591cc7
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b7d016b1a6e91eca1752588825eae6fa2fe0bfdb
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="getlastupdatecount-method-sqlserverdatasource"></a>Метод getLastUpdateCount (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает **логическое** значение, указывающее, включено ли свойство lastUpdateCount.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean getLastUpdateCount()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 **значение true,** Если включено свойство lastUpdateCount. В противном случае — **false**.  
  
## <a name="remarks"></a>Замечания  
 Если свойство lastUpdateCount имеет значение **true**, [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] вернет только последний счетчик обновления из инструкции SQL, переданной серверу. Если свойство lastUpdateCount имеет значение **false**, драйвер вернет все счетчики обновлений, в том числе те, которые возвращены всеми сработавшими триггерами. Если свойство lastUpdateCount не задано, то метод getLastUpdateCount возвращает значение по умолчанию **true**.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  

