---
title: Метод truncate (SQLServerClob) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerClob.truncate
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ea3b2a03-387e-49d7-a4d6-ca6a6a354c90
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3e9f1f7c220fecf512fbed2b8cbcac0c7745d98e
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80908480"
---
# <a name="truncate-method-sqlserverclob"></a>Метод truncate (SQLServerClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Выполняет усечение объекта CLOB до заданной длины.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void truncate(long len)  
```  
  
#### <a name="parameters"></a>Параметры  
 *len*  
  
 Длина в символах, до которой усекается объект CLOB.  
  
## <a name="exceptions"></a>Исключения  
 java.sql.SQLException  
  
## <a name="remarks"></a>Remarks  
 Этот метод truncate задается с помощью метода truncate в интерфейсе java.sql.Clob.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-methods.md)   
 [Элементы SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-members.md)   
 [Класс SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-class.md)  
  
  
