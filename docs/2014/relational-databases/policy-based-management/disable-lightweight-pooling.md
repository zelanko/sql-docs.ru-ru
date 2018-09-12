---
title: Отключение использования упрощенных пулов | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 481bb43d-6fe5-497c-9096-971fb6bf733b
caps.latest.revision: 12
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 97d260fdba2f9f88f6096baf3f553f94c4e1387d
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2018
ms.locfileid: "43808450"
---
# <a name="disable-lightweight-pooling"></a>Отключение использования упрощенных пулов
  Это правило проверяет отключение использования упрощенных пулов на сервере. Значение параметра lightweightpooling, равное 1, приводит к переключению [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в режим волокон для планирования. Режим волокон предназначен для ситуаций, когда важным узким местом, ограничивающим производительность, является переключение контекста рабочих потоков UMS. Поскольку такая ситуация является нестандартной, использование режима волокон редко увеличивает производительность или масштабируемость типичной системы.  
  
## <a name="best-practices-recommendations"></a>Рекомендации  
 Параметр использования упрощенных пулов следует включать только после тщательного тестирования и после оценки всех других возможностей настройки, притом что переключение контекста представляет собой проблему в определенной среде.  
  
 Использовать планирование в режиме волокон для выполнения обычных операций не рекомендуется, поскольку это может привести к снижению производительности, мешая нормальной работе переключения контекста. Кроме того, некоторые компоненты [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , которые используют локальное хранилище потоков (TLS) или объекты, принадлежащие потокам, такие как мьютексы (тип объекта ядра Win32), не выполняются правильно в режиме волокон.  
  
 Чтобы отключить использование упрощенных пулов, выполните следующую инструкцию и перезапустите компонент [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].  
  
```  
sp_configure 'show advanced options', 1;  
GO  
sp_configure 'lightweightpooling', 0;  
GO  
RECONFIGURE;  
GO  
```  
  
## <a name="for-more-information"></a>Дополнительные сведения см. в разделе  
 [Параметр конфигурации сервера «использование упрощенных пулов»](../../database-engine/configure-windows/lightweight-pooling-server-configuration-option.md)  
  
## <a name="see-also"></a>См. также  
 [Наблюдение с помощью управления на основе политик и принудительное применение рекомендаций с помощью управления на основе политик](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
