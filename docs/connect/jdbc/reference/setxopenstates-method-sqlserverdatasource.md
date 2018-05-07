---
title: Метод setXopenStates (SQLServerDataSource) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerDataSource.setXopenStates
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 9723591f-e987-426f-b70a-07f5c70dc094
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 355fb7a9ede35edd70084ad11d9c9c838f03e8a4
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="setxopenstates-method-sqlserverdatasource"></a>Метод setXopenStates (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Наборы **логическое** значение, указывающее, включено ли преобразование состояний SQL в состояния, соответствующие стандарту xopen.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setXopenStates(boolean xopenStates)  
```  
  
#### <a name="parameters"></a>Параметры  
 *xopenStates*  
  
 **значение true,** Если включено преобразование состояний SQL в состояния, соответствующие стандарту xopen. В противном случае — **false**.  
  
## <a name="remarks"></a>Замечания  
 Если свойство xopenStates имеет значение **true**, [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] состояний SQL преобразует с xopen. Значение по умолчанию — **false**, что драйвер JDBC для формирования коды состояний SQL 99. Если состояние xopenStates не задано, [getXopenStates](../../../connect/jdbc/reference/getxopenstates-method-sqlserverdatasource.md) метод возвращает значение по умолчанию **false**.  
  
## <a name="see-also"></a>См. также  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
