---
title: Метод setXopenStates (SQLServerDataSource) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.setXopenStates
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 9723591f-e987-426f-b70a-07f5c70dc094
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3e63dbb2ef8864c07bf1deb58e99a08ea70fafdf
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67972063"
---
# <a name="setxopenstates-method-sqlserverdatasource"></a>Метод setXopenStates (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Задание значения **Boolean**, определяющее, включено ли преобразование состояний SQL в состояния, совместимые с XOPEN.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setXopenStates(boolean xopenStates)  
```  
  
#### <a name="parameters"></a>Параметры  
 *xopenStates*  
  
 Значение **true**, если включено преобразование состояний SQL в состояния, совместимые с XOPEN. В противном случае — **false**.  
  
## <a name="remarks"></a>Remarks  
 Если свойство xopenStates имеет значение **true**, то драйвер [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] будет выполнять преобразование состояний SQL в состояния, совместимые с XOPEN. Значение по умолчанию **false**, при котором драйвер JDBC формирует коды состояний SQL 99. Если состояние xopenStates не задано, метод [getXopenStates](../../../connect/jdbc/reference/getxopenstates-method-sqlserverdatasource.md) возвращает значение по умолчанию **false**.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
