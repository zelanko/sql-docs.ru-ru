---
title: Метод position (java.sql.Blob, long) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerBlob.position (java.sql.Blob.long)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ebd005e5-f6c5-4789-87f9-d2fdacd35060
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 70fd642677405adf98cce23826775a0cab45221a
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80923182"
---
# <a name="position-method-javasqlblob-long"></a>Метод position (java.sql.Blob, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает положение указанного шаблона в большом двоичном объекте на основе указанного шаблона и начального индекса.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public long position(java.sql.Blob pattern,  
                     long start)  
```  
  
#### <a name="parameters"></a>Параметры  
 *pattern*  
  
 Шаблон для поиска.  
  
 *start*  
  
 Индекс, с которого начинается поиск.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **long**, указывающее позицию, в которой обнаружен шаблон, или значение "-1", если шаблон не обнаружен.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод position задается с помощью метода position в интерфейсе java.sql.Blob.  
  
## <a name="see-also"></a>См. также:  
 [Метод position (SQLServerBlob)](../../../connect/jdbc/reference/position-method-sqlserverblob.md)   
 [Методы SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-methods.md)   
 [Элементы SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-members.md)   
 [Класс SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-class.md)  
  
  
