---
title: Отключение предусмотренных по умолчанию файлов журнала трассировки | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: c27761e6-75ed-4ee4-a236-0cbc42e500a1
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: a816912147038cd49b35ba29bfec732410c2ca91
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47616052"
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
  
  
