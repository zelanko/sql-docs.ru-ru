---
description: Метод getPacketSize (SQLServerDataSource)
title: Метод getPacketSize (SQLServerDataSource) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getPacketSize
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b2e9f01a-2e51-47e5-90bf-43c62d1be74d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d21f76ecf79406a3016e9891b0fb2af0e2232def
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88435096"
---
# <a name="getpacketsize-method-sqlserverdatasource"></a>Метод getPacketSize (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает текущий размер сетевого пакета в байтах, используемый для обмена данными с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public int getPacketSize()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение типа **int**, содержащее текущий размер сетевого пакета.  
  
## <a name="remarks"></a>Remarks  
 Если свойство packetSize не задано, метод getPacketSize возвращает значение по умолчанию (8000).  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
