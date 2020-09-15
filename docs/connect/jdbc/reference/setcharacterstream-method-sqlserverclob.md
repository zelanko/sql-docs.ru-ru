---
description: Метод setCharacterStream (SQLServerClob)
title: Метод setCharacterStream (SQLServerClob) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerClob.setCharacterStream
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: c02778f2-6681-4a84-a58b-2bcfac4233e4
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f79891e2a2492a225896495651f8f0746353e6a5
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88432236"
---
# <a name="setcharacterstream-method-sqlserverclob"></a>Метод setCharacterStream (SQLServerClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает поток для записи символов Юникода в объект CLOB, начиная с заданной позиции.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.io.Writer setCharacterStream(long pos)  
```  
  
#### <a name="parameters"></a>Параметры  
 *pos*  
  
 Позиция, с которой начинается запись в объект CLOB.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Поток, в который можно записывать символы в кодировке Юникод.  
  
## <a name="exceptions"></a>Исключения  
 java.sql.SQLException  
  
## <a name="remarks"></a>Remarks  
 Этот метод setCharacterStream задается с помощью метода setCharacterStream в интерфейсе java.sql.Clob.  
  
 Символьные данные в большом двоичном объекте перезаписываются модулем записи, начиная с указанной позиции, и могут превысить начальную длину объекта CLOB. Если указать значение позиции+1, будут добавлены символы. Если указать значение позиции+2 и более (либо нулевое или отрицательное значение), то создается ошибка позиции.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-methods.md)   
 [Элементы SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-members.md)   
 [Класс SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-class.md)  
  
  
