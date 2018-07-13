---
title: Свойства безопасности | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- security [Analysis Services], properties
- SecurityPackageList property
- BuiltinAdminsAreServerAdmins property
- DisableClientImpersonation property
- ErrorMessageMode property
- RequiredProtectionLevel property
- ServiceAccountIsServerAdmin property
- RequireClientAuthentication property
ms.assetid: 2fc7fe10-0cbb-49ac-aa8c-8ec3f7a7705f
caps.latest.revision: 15
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 28553d897d6e3c8b9672e2b16695c9a8924c0d05
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37200224"
---
# <a name="security-properties"></a>Свойства безопасности
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] поддерживают свойства сервера безопасности, перечисленные в следующей таблице. Дополнительные сведения о дополнительных свойствах сервера и об их настройке см. в разделе [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md).  
  
 **Область применения:** многомерный и табличный режим сервера  
  
## <a name="properties"></a>Свойства  
 `RequireClientAuthentication`  
 Логическое свойство, указывает, требуется ли проверка подлинности клиента.  
  
 Значение по умолчанию True означает, что проверка подлинности необходима.  
  
 `SecurityPackageList`  
 Строковое свойство, содержащее разделенный запятыми список пакетов SSPI, при помощи которых сервер проверяет подлинность клиентов.  
  
 `DisableClientImpersonation`  
 Логическое свойство, указывает, отключено ли олицетворение клиента (например, хранимые процедуры).  
  
 Значение по умолчанию False означает, что олицетворение клиента включено.  
  
 `BuiltinAdminsAreServerAdmins`  
 Логическое свойство, указывает, являются ли члены группы администраторов локального компьютера администраторами служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
 `ServiceAccountIsServerAdmin`  
 Логическое свойство, указывает, является ли учетная запись службы администратором сервера.  
  
 Значение по умолчанию True означает, что учетная запись службы является администратором сервера.  
  
 `ErrorMessageMode`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `DataProtection\ RequiredProtectionLevel`  
 Целочисленное 32-разрядное свойство со знаком, определяющее требуемый уровень защиты для всех запросов клиентов. Возможные значения этого свойства перечислены в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*0*|Нет, допускается открытый текст.|  
|*1*|Значение по умолчанию. Открытый текст не регистрируется.|  
|*2*|Допускается подписанный открытый текст (более слабая защита, чем шифрование).|  
  
 `AdministrativeDataProtection\ RequiredProtectionLevel`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
## <a name="see-also"></a>См. также  
 [Настройка свойств сервера в службах Analysis Services](server-properties-in-analysis-services.md)   
 [Определение режима работы сервера экземпляра служб Analysis Services](../instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
