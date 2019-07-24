---
title: Метод Сетворкстатионид (SQLServerDataSource) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.setWorkstationID
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: c1093615-90bf-4918-9f05-8abd765ffb03
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 08b09958276a5cc7f7cc3de6e56f7d7336ca9e64
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67972032"
---
# <a name="setworkstationid-method-sqlserverdatasource"></a>Метод setWorkstationID (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Задает имя клиентского компьютера, используемое для соединения с источником данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setWorkstationID(java.lang.String workstationID)  
```  
  
#### <a name="parameters"></a>Параметры  
 *workstationID*  
  
 Значение **String**, содержащее имя клиентского компьютера.  
  
## <a name="remarks"></a>Remarks  
 Идентификатор workstationID — это имя клиентского компьютера или рабочей станции. Если свойство Воркстатионид не задано, значение по умолчанию создается путем вызова метода Инетаддресс. (). @ HostName (). Если функция-имя возвращает пустое значение, вызывается метод Жесостаддресс (). toString ().  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
