---
title: Метод getPacketSize (SQLServerDataSource) | Документы Microsoft
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
ms.topic: conceptual
apiname:
- SQLServerDataSource.getPacketSize
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b2e9f01a-2e51-47e5-90bf-43c62d1be74d
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9a320d10b6dab2335226087f97d54edc213d4b50
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="getpacketsize-method-sqlserverdatasource"></a>Метод getPacketSize (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает текущий размер сетевого пакета, используемый для связи с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)], указанного в байтах.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public int getPacketSize()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 **Int** значение, содержащее текущий размер сетевого пакета.  
  
## <a name="remarks"></a>Замечания  
 Если свойство packetSize не задано, метод getPacketSize возвращает значение по умолчанию 8000.  
  
## <a name="see-also"></a>См. также  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
