---
title: Метод getLastUpdateCount (SQLServerDataSource) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getLastUpdateCount
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 4c4fbb24-0b02-42da-928c-a903bb591cc7
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e0d284e02be13af60bf7d8e7d447835f7eccd90a
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "67982601"
---
# <a name="getlastupdatecount-method-sqlserverdatasource"></a>Метод getLastUpdateCount (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращение значения **Boolean**, определяющее, включено ли свойство lastUpdateCount.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean getLastUpdateCount()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **true**, если включено свойство lastUpdateCount. В противном случае — **false**.  
  
## <a name="remarks"></a>Remarks  
 Если для свойства lastUpdateCount задано значение **true**, то драйвер [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] вернет только последний счетчик обновления из инструкции SQL, переданной серверу. Если свойство lastUpdateCount имеет значение **false**, то драйвер вернет все счетчики обновлений, в том числе и те, которые возвращены всеми сработавшими триггерами. Если свойство lastUpdateCount не задано, то метод getLastUpdateCount возвращает значение по умолчанию **true**.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
