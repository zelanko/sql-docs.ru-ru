---
title: Метод SetEnable (класс класс servernetworkprotocolipaddress) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetEnable Method (ServerNetworkProtocolIPAddress Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetEnable method
ms.assetid: baa86deb-95dd-416f-b2c7-cec1dfb91ab4
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: d4c542aa1491710d49ec4c24c027e69f2eef24a9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62643123"
---
# <a name="setenable-method-servernetworkprotocolipaddress-class"></a>Метод SetEnable (класс ServerNetworkProtocolIPAddress)
  Задействует IP-адрес.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object  
.SetEnable()  
  
```  
  
## <a name="parts"></a>Компоненты  
 *объектами*  
 A [класса ServerNetworkProtocolIPAdress](servernetworkprotocolipaddress-class.md) , который представляет IP-адрес сетевого протокола для экземпляра [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Значение `uint32`, равное 0, если служба изменена успешно, и 1, если запрос не поддерживается. Любое другое значение указывает на ошибку.  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>См. также:  
 [Конфигурирование сетевых протоколов сервера и сетевых библиотек](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
