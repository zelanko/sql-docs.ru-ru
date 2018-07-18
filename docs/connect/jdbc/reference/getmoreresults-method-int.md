---
title: Метод getMoreResults (int) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerStatement.getMoreResults (int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 6419e5a8-8b3a-4d5b-8226-95865c52c723
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 75609ec8f24674dd7ff9d1a6724cbc458be47f84
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32837749"
---
# <a name="getmoreresults-method-int"></a>Метод getMoreResults (int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Переходит к следующему результату [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) объекта и сделками с какой-либо открытых результат задать объекты в соответствии с инструкциями, заданными указанным режимом.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final boolean getMoreResults(int mode)  
```  
  
#### <a name="parameters"></a>Параметры  
 *Режим*  
  
 **Int** , указывающее способ обработки объекты открытые результирующего набора. Это должна быть одна из следующих констант:  
  
 CLOSE_CURRENT_RESULT  
  
 KEEP_CURRENT_RESULT (не поддерживается драйвером JDBC)  
  
 CLOSE_ALL_RESULTS  
  
## <a name="return-value"></a>Возвращаемое значение  
 **значение true,** если возвращенный результат является результирующим набором. В противном случае — **false**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод getMoreResults указывается с помощью метода getMoreResults в интерфейсе java.sql.Statement.  
  
 Если метод getMoreResults вызывается перед получением результатов, он ведет себя в соответствии с *режим* аргумента и переходит к следующему результату.  
  
> [!NOTE]  
>  Драйвер JDBC не поддерживает использование константы KEEP_CURRENT_RESULT. Если эта константа используется, вызывается исключение.  
  
## <a name="see-also"></a>См. также  
 [Метод getMoreResults &#40;SQLServerStatement&#41;](../../../connect/jdbc/reference/getmoreresults-method-sqlserverstatement.md)   
 [Члены SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Класс SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
