---
title: Метод setTrustManagerClass (SQLServerDataSource) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.setTrustManagerClass
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ''
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9d197589cb1b4702404ce8ba22200a7bde7e4da4
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "67972265"
---
# <a name="settrustmanagerclass-method-sqlserverdatasource"></a>Метод setTrustManagerClass (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Устанавливает строковое значение свойства подключения TrustManagerClass.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setTrustManagerClass(java.lang.String trustManagerClass)  
```  
  
#### <a name="parameters"></a>Параметры  
 *trustManagerClass*  
  
 **Строка**, содержащая полное имя класса настраиваемого интерфейса javax.net.ssl.TrustManager.
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
