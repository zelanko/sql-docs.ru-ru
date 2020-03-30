---
title: Метод getSendStringParametersAsUnicode (SQLServerDataSource) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getSendStringParametersAsUnicode
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 3836d0ab-c3fb-41ff-bb89-10389594ae51
author: MightyPen
ms.author: genemi
ms.openlocfilehash: df27a5368dfea7f417fb84e2ebe38a8987165aec
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "67979973"
---
# <a name="getsendstringparametersasunicode-method-sqlserverdatasource"></a>Метод getSendStringParametersAsUnicode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращение значения **boolean**, указывающего, разрешена ли отправка параметров на сервер в Юникоде.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean getSendStringParametersAsUnicode()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **true**, если строковые параметры отправляются на сервер в Юникоде. В противном случае — **false**.  
  
## <a name="remarks"></a>Remarks  
 Если свойство sendStringParametersAsUnicode имеет значение **true** (значение по умолчанию), то строковые параметры отправляются на сервер в Юникоде. Если для свойства sendStringParametersAsUnicode задано значение **false**, то строковые параметры отправляются в формате ASCII/MBCS, а не в Юникоде. Если свойство sendStringParametersAsUnicode не задано, getSendStringParametersAsUnicode возвращает **true**.  
  
 Дополнительные сведения о свойстве подключения sendStringParametersAsUnicode см. в статье [Настройка свойств подключения](../../../connect/jdbc/setting-the-connection-properties.md).  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
