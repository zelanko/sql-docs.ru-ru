---
title: Службы Analysis Services свойства безопасности | Документация Майкрософт
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 31191e266b017400b8b8aceb2eb912f9bebca3d5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "68163464"
---
# <a name="security-properties"></a>Свойства безопасности
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] поддерживают свойства сервера безопасности, перечисленные в следующей таблице. Дополнительные сведения о дополнительных свойствах сервера и их настройке см. в разделе [Свойства сервера в службах Analysis Services](../../analysis-services/server-properties/server-properties-in-analysis-services.md).  
  
 **Применимо к:** Многомерный и Табличный режим сервера  
  
## <a name="properties"></a>Свойства  
 **RequireClientAuthentication**  
 Логическое свойство, указывает, требуется ли проверка подлинности клиента.  
  
 Значение по умолчанию True означает, что проверка подлинности необходима.  
  
 **SecurityPackageList**  
 Строковое свойство, содержащее разделенный запятыми список пакетов SSPI, при помощи которых сервер проверяет подлинность клиентов.  
  
 **DisableClientImpersonation**  
 Логическое свойство, указывает, отключено ли олицетворение клиента (например, хранимые процедуры).  
  
 Значение по умолчанию False означает, что олицетворение клиента включено.  
  
 **BuiltinAdminsAreServerAdmins**  
 Логическое свойство, указывает, являются ли члены группы администраторов локального компьютера администраторами служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
 **ServiceAccountIsServerAdmin**  
 Логическое свойство, указывает, является ли учетная запись службы администратором сервера.  
  
 Значение по умолчанию True означает, что учетная запись службы является администратором сервера.  
  
 **ErrorMessageMode**  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **DataProtection\ RequiredProtectionLevel**  
 Целочисленное 32-разрядное свойство со знаком, определяющее требуемый уровень защиты для всех запросов клиентов. Возможные значения этого свойства перечислены в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*0*|Нет, допускается открытый текст.|  
|*1*|Значение по умолчанию. Открытый текст не регистрируется.|  
|*2*|Допускается подписанный открытый текст (более слабая защита, чем шифрование).|  
  
 **AdministrativeDataProtection\ RequiredProtectionLevel**  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
## <a name="see-also"></a>См. также  
 [Свойства сервера в службах Analysis Services](../../analysis-services/server-properties/server-properties-in-analysis-services.md)   
 [Определение режима работы сервера экземпляра служб Analysis Services](../../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
