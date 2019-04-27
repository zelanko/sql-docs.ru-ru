---
title: Параметр конфигурации сервера "Ole Automation Procedures" | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- Ole Automation Procedures option
ms.assetid: e8982e05-4984-4406-9760-285e8c028ddf
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: f00c238dfb32089261c51936b3937b0657c58b08
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62782032"
---
# <a name="ole-automation-procedures-server-configuration-option"></a>Параметр конфигурации сервера «Ole Automation Procedures»
  C помощью параметра `Ole Automation Procedures` можно указать возможность создания экземпляров объектов OLE-автоматизации в пакетах [!INCLUDE[tsql](../../includes/tsql-md.md)]. Этот параметр также можно настроить с помощью управления на основе политики или с помощью хранимой процедуры **sp_configure** . Дополнительные сведения см. в разделе [Surface Area Configuration](../../relational-databases/security/surface-area-configuration.md).  
  
 Параметр `Ole Automation Procedures` может принимать следующие значения:  
  
 0  
 Процедуры OLE-автоматизации отключены. По умолчанию для новых экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 1  
 Процедуры OLE-автоматизации включены.  
  
 После включения процедур OLE-автоматизации процедура **sp_OACreate** запустит общую среду выполнения OLE.  
  
 Текущее значение `Ole Automation Procedures` параметр можно просмотреть и изменить с помощью **sp_configure** системной хранимой процедуры.  
  
## <a name="examples"></a>Примеры  
 В следующем примере показан просмотр текущего значения параметра OLE Automation procedures.  
  
```  
EXEC sp_configure 'Ole Automation Procedures';  
GO  
```  
  
 В следующем примере показано включение процедур OLE-автоматизации.  
  
```  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'Ole Automation Procedures', 1;  
GO  
RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [RECONFIGURE (Transact-SQL)](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [Surface Area Configuration](../../relational-databases/security/surface-area-configuration.md)   
 [Параметры конфигурации сервера (SQL Server)](server-configuration-options-sql-server.md)  
  
  
