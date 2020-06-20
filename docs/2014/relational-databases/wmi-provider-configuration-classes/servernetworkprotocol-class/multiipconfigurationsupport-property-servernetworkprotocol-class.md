---
title: Свойство MultiIpConfigurationSupport (класс класс servernetworkprotocol) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- MultiIpConfigurationSupport Property (ServerNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- MultiIpConfigurationSupport property
ms.assetid: 442c6133-4038-42db-a67d-2631285ac76b
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 80401a607c9155451a869082162affcca401ebca
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85059907"
---
# <a name="multiipconfigurationsupport-property-servernetworkprotocol-class"></a>Свойство MultiIpConfigurationSupport (класс ServerNetworkProtocol)
  Возвращает логическое свойство, определяющее, поддерживаются ли несколько IP-адресов сетевым протоколом сервера.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object  
.MultiIpConfigurationSupport [= value]  
```  
  
## <a name="parts"></a>Компоненты  
 *object*  
 Объект [Свойства ProtocolName (класс класс servernetworkprotocol)](servernetworkprotocol-class.md) , представляющий сетевой протокол, используемый экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Логическое значение, определяющее, поддерживает ли сетевой протокол сервера несколько IP-адресов: `true`, если поддерживает; в противном случае — `false`.  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>См. также:  
 [Конфигурирование сетевых протоколов сервера и сетевых библиотек](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
