---
title: Метод getWorkstationID (SQLServerDataSource) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getWorkstationID
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f6a701de-a8fa-4668-9310-99a8c6e32c88
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2848ed26d2ce9df960170d3f7a1d3e4c49b630ab
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80910170"
---
# <a name="getworkstationid-method-sqlserverdatasource"></a>Метод getWorkstationID (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает имя клиентского компьютера, используемое для соединения с источником данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.lang.String getWorkstationID()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **String**, содержащее имя клиентского компьютера.  
  
## <a name="remarks"></a>Remarks  
 Идентификатор workstationID — это имя клиентского компьютера или рабочей станции. Если свойство workstationID не задано, то значение по умолчанию создается путем вызова метода InetAddress.getLocalHost().getHostName(). Если getHostName возвращает пустое значение, вызывается метод getHostAddress().toString().  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
