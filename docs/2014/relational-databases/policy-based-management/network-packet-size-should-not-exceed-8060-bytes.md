---
title: Размер сетевого пакета не должен превышать 8060 байт | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 86db5da1-afe4-4fbb-8bf8-33cedc7e4361
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 1d66ba3298b2346e2ec139f27ec53d6104ad0ac9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62625820"
---
# <a name="network-packet-size-should-not-exceed-8060-bytes"></a>Размер сетевого пакета не должен превышать 8060 байт
  Если значение, заданное для параметра хранимой процедуры sp_configure 'network packet size', или размер пакета любого вошедшего в систему пользователя превышает 8 060 байт, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполняет другие операции выделения памяти. Это может привести к увеличению виртуального адресного пространства процессов, которое не зарезервировано для буферного пула.  
  
## <a name="best-practices-recommendations"></a>Рекомендации  
 Размер сетевого пакета не должен превышать 8 060 байт.  
  
## <a name="for-more-information"></a>Дополнительные сведения см. в разделе  
 [Статья 903002 базы знаний Майкрософт](https://go.microsoft.com/fwlink/?linkid=117749)  
  
## <a name="see-also"></a>См. также:  
 [Наблюдение с помощью управления на основе политик и принудительное применение рекомендаций с помощью управления на основе политик](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
