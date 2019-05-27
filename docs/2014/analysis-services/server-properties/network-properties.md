---
title: Свойства сети | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- LingerTimeout property
- EnableNagleAlgorithm property
- MinPendingAcceptExCount property
- MaxPendingSendCount property
- EnableBinaryXML property
- MinPendingReceiveCount property
- MaxCompletedReceiveCount property
- DisableNonblockingMode property
- RequestSizeThreshold property
- CompressionLevel property
- ReceiveBufferSize property
- EnableCompression property
- ServerSendTimeout property
- IPV4Support property
- MaxPendingReceiveCount property
- MaxPendingAcceptExCount property
- IPV6Support property
- MaxAllowedRequestSize property
- ServerReceiveTimeout property
- EnableLingerOnClose property
- InitialConnectTimeout property
- SendBufferSize property
- ScatterReceiveMultiplier property
- network properties [Analysis Services]
ms.assetid: ef4251e2-abe5-4c5b-9868-7549782d0244
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 882b5fc60020423e19f68fda40273b7c944bd4f5
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66068877"
---
# <a name="network-properties"></a>Свойства сети
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] поддерживают свойства сервера, перечисленные в следующих таблицах. Дополнительные сведения о дополнительных свойствах сервера и об их настройке см. в разделе [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md).  
  
 **Применимо к:** Многомерный и Табличный режим сервера  
  
## <a name="general"></a>Общие  
 `ListenOnlyOnLocalConnections`  
 Логическое свойство, указывающее прослушивание только локальных соединений, например локального сервера.  
  
## <a name="listener"></a>Средство прослушивания  
 `IPV4Support`  
 Свойство с 32-разрядным целочисленным значением со знаком, определяющее поддержку протокола IPv4. Это свойство имеет одно из значений, содержащихся в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*0*|Протокол IPv4 отключен; подключение клиентов невозможно.|  
|*1*|(По умолчанию) необходим протокол IPv4; сервер невозможно запустить без прослушивания по IPv4.|  
|*2*|Дополнительный протокол IPv4; сервер пытается прослушать по протоколу IPv4, но запускается в любом случае.|  
  
 `IPV6Support`  
 Свойство с 32-разрядным целочисленным значением со знаком, определяющее поддержку протокола IPv6. Это свойство имеет одно из значений, содержащихся в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*0*|Протокол IPv6 отключен; подключение клиентов невозможно.|  
|*1*|(По умолчанию) необходим протокол IPv6; сервер невозможно запустить без прослушивания по IPv6.|  
|*2*|Дополнительный протокол IPv6; сервер пытается прослушать по протоколу IPv6, но запускается в любом случае.|  
  
 `MaxAllowedRequestSize`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `RequestSizeThreshold`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `ServerReceiveTimeout`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `ServerSendTimeout`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
## <a name="requests"></a>Запросы  
 `EnableBinaryXML`  
 Логическое свойство, определяющее, распознает ли сервер запросы в двоичном XML-формате.  
  
 `EnableCompression`  
 Логическое свойство, определяющее сжатие запросов.  
  
## <a name="responses"></a>Responses  
 `CompressionLevel`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `EnableBinaryXML`  
 Логическое свойство, определяющее включение на сервере двоичных XML-ответов.  
  
 `EnableCompression`  
 Логическое свойство, определяющее сжатие ответов клиентам.  
  
## <a name="tcp"></a>TCP  
 `InitialConnectTimeout`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `MaxCompletedReceiveCount`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `MaxPendingAcceptExCount`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `MaxPendingReceiveCount`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `MaxPendingSendCount`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `MinPendingAcceptExCount`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `MinPendingReceiveCount`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `ScatterReceiveMultiplier`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `SocketOptions\ DisableNonblockingMode`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `SocketOptions\ EnableLingerOnClose`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `SocketOptions\EnableNagleAlgorithm`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `SocketOptions\ LingerTimeout`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `SocketOptions\ ReceiveBufferSize`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `SocketOptions\ SendBufferSize`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
## <a name="see-also"></a>См. также  
 [Настройка свойств сервера в службах Analysis Services](server-properties-in-analysis-services.md)   
 [Определение режима работы сервера экземпляра служб Analysis Services](../instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
