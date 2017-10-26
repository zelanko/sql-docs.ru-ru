---
title: "Метод setSendStringParametersAsUnicode (SQLServerDataSource) | Документы Microsoft"
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
- SQLServerDataSource.setSendStringParametersAsUnicode
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 49198d63-76cb-4843-8d04-e49b1fbb6916
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 554c7e2483e96e27de627f764193a1d4fcabb6dd
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="setsendstringparametersasunicode-method-sqlserverdatasource"></a>Метод setSendStringParametersAsUnicode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Наборы **логическое** значение, указывающее, включена ли отправка параметров на сервер в Юникоде.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setSendStringParametersAsUnicode(boolean sendStringParametersAsUnicode)  
```  
  
#### <a name="parameters"></a>Параметры  
 *sendStringParametersAsUnicode*  
  
 **значение true,** Если строковые параметры отправляются на сервер в Юникоде. В противном случае — **false**.  
  
## <a name="remarks"></a>Замечания  
 Если свойство sendStringParametersAsUnicode имеет значение **true**, который является значением по умолчанию, строковые параметры отправляются на сервер в Юникоде. Если для свойства sendStringParametersAsUnicode задано значение **false** строковые параметры отправляются на сервер в формате ASCII/MBCS, а не в ЮНИКОДЕ. Если sendStringParametersAsUnicode не задано, [getSendStringParametersAsUnicode](../../../connect/jdbc/reference/getsendstringparametersasunicode-method-sqlserverdatasource.md) возвращает значение по умолчанию **true**.  
  
 Дополнительные сведения о свойстве соединения sendStringParametersAsUnicode см. в разделе [задание свойств соединения](../../../connect/jdbc/setting-the-connection-properties.md).  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  

