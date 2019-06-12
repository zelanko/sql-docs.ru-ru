---
title: Метод TRUNCATE (SQLServerBlob) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerBlob.truncate
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ef181e04-003a-442a-9b7e-0c508a7cc873
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: ce085032435cfe2bbb95137c12c98ac0f53206b5
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66785041"
---
# <a name="truncate-method-sqlserverblob"></a>Метод truncate (SQLServerBlob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Выполняет усечение большого двоичного объекта до заданной длины.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void truncate(long len)  
```  
  
#### <a name="parameters"></a>Параметры  
 *len*  
  
 Новая длина большого двоичного объекта.  
  
## <a name="exceptions"></a>Исключения  
 java.sql.SQLException  
  
## <a name="remarks"></a>Remarks  
 Этот усечения метод указывается методом усечения в интерфейсе java.sql.Blob.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-methods.md)   
 [Элементы SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-members.md)   
 [Класс SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-class.md)  
  
  
