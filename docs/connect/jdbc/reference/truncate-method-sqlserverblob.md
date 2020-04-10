---
title: Метод truncate (SQLServerBlob) | Документация Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ddcb67b6a679cadaa33775d11987d90a735ca799
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80908478"
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
 Этот метод truncate задается с помощью метода truncate в интерфейсе java.sql.Blob.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-methods.md)   
 [Элементы SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-members.md)   
 [Класс SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-class.md)  
  
  
