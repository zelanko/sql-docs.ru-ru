---
title: Метод (SQLServerResultSet) getUnicodeStream | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerResultSet.getUnicodeStream
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 0dd61865-663b-47e2-b417-e9df418894cc
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 52900f4e9ca91e4dc91ca939f0609ed42bdb1084
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="getunicodestream-method-sqlserverresultset"></a>getUnicodeStream метод (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Получает значение заданного столбца в текущей строке [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объект как поток символов Юникода.  
  
> [!NOTE]  
>  Этот метод является устаревшим в спецификации JDBC, и в случае его вызова создается исключение «не реализовано». Вместо этого следует использовать [getCharacterStream](../../../connect/jdbc/reference/getcharacterstream-method-sqlserverresultset.md) метод.  
  
## <a name="overload-list"></a>Список перегрузок  
  
|Название|Описание|  
|----------|-----------------|  
|[Метод getUnicodeStream &#40;int&#41;](../../../connect/jdbc/reference/getunicodestream-method-int.md)|Получает значение индекса заданного столбца в текущей строке [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объект как поток символов Юникода.|  
|[Метод getUnicodeStream &#40;java.lang.String&#41;](../../../connect/jdbc/reference/getunicodestream-method-java-lang-string.md)|Получает значение имени заданного столбца в текущей строке [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объект как поток символов Юникода.|  
  
## <a name="see-also"></a>См. также  
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
