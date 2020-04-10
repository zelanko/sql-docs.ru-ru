---
title: Метод getXopenStates (SQLServerDataSource) | Документация Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c4367bd0df42400d2fd9352ae86dc43e4e98b801
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80910130"
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
  
  
