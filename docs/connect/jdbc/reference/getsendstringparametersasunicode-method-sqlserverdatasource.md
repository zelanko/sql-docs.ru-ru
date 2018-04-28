---
title: Метод getSendStringParametersAsUnicode (SQLServerDataSource) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
apiname:
- SQLServerDataSource.getSendStringParametersAsUnicode
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 3836d0ab-c3fb-41ff-bb89-10389594ae51
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8286a658b12df7466c2eec2d702c1fc3e005f06f
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="getsendstringparametersasunicode-method-sqlserverdatasource"></a>Метод getSendStringParametersAsUnicode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает **логическое** значение, указывающее, включена ли отправка параметров на сервер в Юникоде.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean getSendStringParametersAsUnicode()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 **значение true,** Если строковые параметры отправляются на сервер в Юникоде. В противном случае — **false**.  
  
## <a name="remarks"></a>Замечания  
 Если свойство sendStringParametersAsUnicode имеет значение **true**, который является значением по умолчанию, строковые параметры отправляются на сервер в Юникоде. Если для свойства sendStringParametersAsUnicode задано значение **false**, строковые параметры отправляются на сервер в формате ASCII/MBCS, а не в ЮНИКОДЕ. Если sendStringParametersAsUnicode не задано, getSendStringParametersAsUnicode возвращает значение по умолчанию **true**.  
  
 Дополнительные сведения о свойстве соединения sendStringParametersAsUnicode см. в разделе [задание свойств соединения](../../../connect/jdbc/setting-the-connection-properties.md).  
  
## <a name="see-also"></a>См. также  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
