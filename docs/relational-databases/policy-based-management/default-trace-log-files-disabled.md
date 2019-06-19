---
title: Отключение предусмотренных по умолчанию файлов журнала трассировки | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: c27761e6-75ed-4ee4-a236-0cbc42e500a1
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 73544b743dbdf4e17961c59eedefa6c4a602c913
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63008031"
---
# <a name="default-trace-log-files-disabled"></a>Отключение предусмотренных по умолчанию файлов журнала трассировки
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Это правило проверяет значение хранимой процедуры sp_configure «default trace enabled», чтобы определить, включена ли трассировка по умолчанию (значение ON (1)) или отключена (значение OFF (0)). Если параметр включен, трассировка по умолчанию предоставляет [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]данные о конфигурации и изменениях DDL. В некоторых случаях эти сведения могут оказаться полезными для клиентов и службы поддержки пользователей [!INCLUDE[msCoName](../../includes/msconame-md.md)] при устранении неполадок с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
## <a name="best-practices-recommendations"></a>Рекомендации  
 Для установки значения параметра «default trace enabled» равным 1 используется хранимая процедура sp_configure.  
  
## <a name="for-more-information"></a>Дополнительные сведения см. в разделе  
 [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
## <a name="see-also"></a>См. также:  
 [Наблюдение с помощью управления на основе политик и принудительное применение рекомендаций с помощью управления на основе политик](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
