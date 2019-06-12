---
title: Метод getResponseBuffering (SQLServerDataSource) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getResponseBuffering()
apilocation:
- SQLServerDataSource.getResponseBuffering()
apitype: Assembly
ms.assetid: 19585a93-88a4-415e-a20e-12ba58cddeaa
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 7ea9552ff9a9bf8d0a591f35670ca7147c67e18d
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66801359"
---
# <a name="getresponsebuffering-method-sqlserverdatasource"></a>Метод getResponseBuffering (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает режим буферизации ответов для этого объекта [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.lang.String getResponseBuffering()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект **строка** , содержит в нижнем регистре **полный** или **адаптивной**.  
  
## <a name="remarks"></a>Remarks  
 Значение **full** указывает на чтение всех результатов с сервера во время выполнения.  
  
 Значение **adaptive** указывает на буферизацию минимального количества данных при необходимости. Значение **adaptive** — это режим буферизации по умолчанию.  
  
 Дополнительные сведения об использовании режима буферизации ответов см. в разделе [Using Adaptive Buffering](../../../connect/jdbc/using-adaptive-buffering.md).  
  
## <a name="see-also"></a>См. также:  
 [Метод setResponseBuffering (SQLServerDataSource)](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverdatasource.md)   
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
