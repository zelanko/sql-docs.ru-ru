---
title: Метод getXopenStates (SQLServerDataSource) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getXopenStates
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: de6fdf6b-8345-4490-b35e-7115b61e782e
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: c0a3859c3195d14243ff570493d3ae04c72d0780
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66768811"
---
# <a name="getxopenstates-method-sqlserverdatasource"></a>Метод getXopenStates (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращение значения **boolean**, определяющее, включено ли преобразование состояний SQL в состояния, совместимые с XOPEN.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean getXopenStates()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **true**, если включено преобразование состояний SQL в состояния, совместимые с XOPEN. В противном случае — **false**.  
  
## <a name="remarks"></a>Remarks  
 Если свойство xopenStates имеет значение **true**, то драйвер [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] будет выполнять преобразование состояний SQL в состояния, совместимые с XOPEN. Значение по умолчанию **false**, при котором драйвер JDBC формирует коды состояний SQL 99. Если состояние xopenStates не задано, метод getXopenStates возвращает значение по умолчанию **false**.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
