---
title: Определение источника пакетов с помощью цифровых подписей | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- signing packages [Integration Services]
- certificates [Integration Services]
- packages [Integration Services], security
- security [Integration Services], certificates
- signing policies [Integration Services]
ms.assetid: a433fbef-1853-4740-9d5e-8a32bc4ffbb2
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 8e1bf17207e57f8488e10c6b37cc7fa876d511b4
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52798916"
---
# <a name="identify-the-source-of-packages-with-digital-signatures"></a>Определение источника пакетов с помощью цифровых подписей
  Пакет служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] может быть подписан цифровым сертификатом, удостоверяющим его происхождение. После подписи пакета цифровым сертификатом службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] проверяют цифровую подпись перед загрузкой пакета. Чтобы службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] проверяли подпись, необходимо задать параметр в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] или в программе **dtexec** (dtexec.exe) либо задать необязательное значение реестра.  
  
## <a name="signing-a-package-with-a-digital-certificate"></a>Подпись пакета цифровым сертификатом  
 Прежде чем подписывать пакет цифровым сертификатом, сертификат необходимо получить или создать. Цифровая подпись пакета возможна только при наличии сертификата. Дополнительные сведения о получении сертификата и подписи им пакета см. в разделе [Подписание пакета цифровым сертификатом](../sign-a-package-by-using-a-digital-certificate.md).  
  
## <a name="setting-an-option-to-check-the-package-signature"></a>Задание параметра для проверки цифровой подписи  
 И среда [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] , и программа **dtexec** позволяют задать параметр, который настраивает проверку цифровой подписи в службе [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] для подписанных пакетов. Выбор средства (среда [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] или программа **dtexec** ) зависит от того, нужно ли проверять все пакеты или лишь некоторые из них.  
  
-   Чтобы во время разработки перед загрузкой проверялась цифровая подпись всех пакетов, установите параметр **Проверять цифровую подпись при загрузке пакета** в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Этот параметр является глобальной настройкой для всех пакетов в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Дополнительные сведения см. в разделе [General Page](../general-page-of-integration-services-designers-options.md).  
  
-   Чтобы проверить цифровую подпись отдельного пакета, укажите `/VerifyS[igned]` параметр при использовании **dtexec** служебная программа для запуска пакета. Дополнительные сведения см. в статье [dtexec Utility](../packages/dtexec-utility.md).  
  
## <a name="setting-a-registry-value-to-check-the-package-signature"></a>Задание значения реестра для проверки цифровой подписи  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] также поддерживают необязательное значение реестра **BlockedSignatureStates**, которое позволяет управлять политикой организации в отношении загрузки подписанных и неподписанных пакетов. Этот параметр препятствует загрузке пакетов, которые не подписаны либо имеют неверную или ненадежную подпись. Дополнительные сведения о задании этого значения реестра см. в разделе [Реализация политики подписывания путем задания параметра реестра](../implement-a-signing-policy-by-setting-a-registry-value.md).  
  
> [!NOTE]  
>  Дополнительный раздел реестра **BlockedSignatureStates** может задавать значение, накладывающее более строгое ограничение, чем параметр цифровой подписи, задаваемый в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] или программе командной строки **dtexec** . В этом случае значение в реестре переопределяет другие параметры.  
  
## <a name="see-also"></a>См. также  
 [Пакеты служб Integration Services (SSIS)](../integration-services-ssis-packages.md)   
 [Общие сведения о безопасности (службы Integration Services)](security-overview-integration-services.md)  
  
  
