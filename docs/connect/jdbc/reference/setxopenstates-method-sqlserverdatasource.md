---
description: Метод setXopenStates (SQLServerDataSource)
title: Метод setXopenStates (SQLServerDataSource) | Документация Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 345f243f6fb712208df336207ee408cd7596b296
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88450620"
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
  
  
