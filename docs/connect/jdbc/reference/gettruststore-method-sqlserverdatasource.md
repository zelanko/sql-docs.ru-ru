---
title: Метод getTrustStore (SQLServerDataSource) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- getTrustStore Method (SQLServerDataSource)
apilocation:
- getTrustStore Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: 8f5850e4-8627-49a8-ba0e-b1f4014322a5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 561148cb1492457c4528bd1fdbf60e66233c6b6e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47708872"
---
# <a name="gettruststore-method-sqlserverdatasource"></a>Метод getTrustStore (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает путь к файлу сертификата trustStore (включая имя файла).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.lang.String getTrustStore()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение типа **String**, содержащее путь к файлу сертификата trustStore (включая имя файла), или значение NULL, если значение не задано.  
  
## <a name="remarks"></a>Remarks  
 Если свойство trustStore не задано, то метод [getTrustStore](../../../connect/jdbc/reference/gettruststore-method-sqlserverdatasource.md) возвращает значение NULL.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
