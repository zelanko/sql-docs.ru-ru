---
title: "Определение источника пакетов с помощью цифровых подписей | Microsoft Docs"
ms.custom: ""
ms.date: "08/24/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "подписывание пакетов [службы Integration Services]"
  - "сертификаты [службы Integration Services]"
  - "пакеты [службы Integration Services], безопасность"
  - "безопасность [Integration Services], сертификаты"
  - "политики подписывания [службы Integration Services]"
ms.assetid: a433fbef-1853-4740-9d5e-8a32bc4ffbb2
caps.latest.revision: 46
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 46
---
# Определение источника пакетов с помощью цифровых подписей
  Пакет служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] может быть подписан цифровым сертификатом, удостоверяющим его происхождение. После подписи пакета цифровым сертификатом службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] проверяют цифровую подпись перед загрузкой пакета. Чтобы службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] проверяли подпись, необходимо задать параметр в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] или в программе **dtexec** (dtexec.exe) либо задать необязательное значение реестра.  
  
## Подпись пакета цифровым сертификатом  
 Прежде чем подписывать пакет цифровым сертификатом, сертификат необходимо получить или создать. Цифровая подпись пакета возможна только при наличии сертификата. Дополнительные сведения о получении сертификата и подписи им пакета см. в разделе [Подписание пакета цифровым сертификатом](../../integration-services/packages/sign-a-package-by-using-a-digital-certificate.md).  
  
## Задание параметра для проверки подписи пакета  
 И среда [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], и программа **dtexec** позволяют задать параметр, который настраивает проверку цифровой подписи в службе [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] для подписанных пакетов. Выбор средства (среда [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] или программа **dtexec**) зависит от того, нужно ли проверять все пакеты или лишь некоторые из них.  
  
-   Чтобы во время разработки перед загрузкой проверялась цифровая подпись всех пакетов, установите параметр **Проверять цифровую подпись при загрузке пакета** в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Этот параметр является глобальной настройкой для всех пакетов в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].
  
-   Чтобы проверить цифровую подпись отдельного пакета, укажите параметр **/VerifyS[igned]** при запуске программы **dtexec** для запуска пакета. Дополнительные сведения см. в статье [dtexec Utility](../../integration-services/packages/dtexec-utility.md).  
  
## Задание значения реестра для проверки подписи пакета  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] также поддерживают необязательное значение реестра **BlockedSignatureStates**, которое позволяет управлять политикой организации в отношении загрузки подписанных и неподписанных пакетов. Этот параметр препятствует загрузке пакетов, которые не подписаны либо имеют неверную или ненадежную подпись. Дополнительные сведения о задании этого значения реестра см. в разделе [Реализация политики подписывания путем задания параметра реестра](../../integration-services/packages/implement-a-signing-policy-by-setting-a-registry-value.md).  
  
> **ПРИМЕЧАНИЕ.** Дополнительное значение реестра **BlockedSignatureStates** может задавать настройку, накладывающую более строгое ограничение, чем параметр цифровой подписи, задаваемый в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] или программе командной строки **dtexec**. В этом случае значение в реестре переопределяет другие параметры.  
  
## См. также:  
 [Пакеты служб Integration Services (SSIS)](../../integration-services/integration-services-ssis-packages.md)   
 [Общие сведения о безопасности (службы Integration Services)](../../integration-services/security/security-overview-integration-services.md)  
  
  