---
title: Параметр конфигурации сервера "EKM provider enabled" | Документы Майкрософт
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- external encryption provider
helpviewer_keywords:
- EKM provider enabled option
ms.assetid: da58ed50-3a13-4172-9065-960559d8f383
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 136056f848c85c2fbe8c572a5866c4e23b3a85b5
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62782223"
---
# <a name="ekm-provider-enabled-server-configuration-option"></a>Включенный параметр конфигурации сервера поставщика расширенного управления ключами
  Параметр `EKM provider enabled` управляет поддержкой устройства расширенного управления ключами в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. По умолчанию этот параметр отключен.  
  
 Чтобы включить или отключить эту функцию, выполните одну из приведенных ниже команд `sp_configure`:  
  
```  
/* Enable the external encryption provider option */  
sp_configure 'EKM provider enabled', 1  
/* Disable the external encryption provider option */  
sp_configure 'EKM provider enabled', 0  
```  
  
> [!NOTE]  
>  Этот параметр не включен ни в один из выпусков [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Перечень функций, поддерживаемых в разных выпусках [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в разделе [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
## <a name="see-also"></a>См. также  
 [Расширенное управление ключами &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md)   
 [Параметры конфигурации сервера (SQL Server)](server-configuration-options-sql-server.md)   
 [Наблюдение за использованием ресурсов (системный монитор)](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)   
 [sp_configure (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [RECONFIGURE (Transact-SQL)](/sql/t-sql/language-elements/reconfigure-transact-sql)  
  
  
