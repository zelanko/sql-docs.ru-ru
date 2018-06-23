---
title: Размер сетевого пакета не должен превышать 8060 байт | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 86db5da1-afe4-4fbb-8bf8-33cedc7e4361
caps.latest.revision: 8
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 4a0502a64ab55ae825d8b8d7f017472f34851e17
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36109475"
---
# <a name="network-packet-size-should-not-exceed-8060-bytes"></a>Размер сетевого пакета не должен превышать 8060 байт
  Если значение, заданное для параметра хранимой процедуры sp_configure 'network packet size', или размер пакета любого вошедшего в систему пользователя превышает 8 060 байт, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполняет другие операции выделения памяти. Это может привести к увеличению виртуального адресного пространства процессов, которое не зарезервировано для буферного пула.  
  
## <a name="best-practices-recommendations"></a>Рекомендации  
 Размер сетевого пакета не должен превышать 8 060 байт.  
  
## <a name="for-more-information"></a>Дополнительные сведения см. в разделе  
 [Статья 903002 базы знаний Майкрософт](http://go.microsoft.com/fwlink/?linkid=117749)  
  
## <a name="see-also"></a>См. также  
 [Наблюдение с помощью управления на основе политик и принудительное применение рекомендаций с помощью управления на основе политик](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  