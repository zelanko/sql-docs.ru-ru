---
title: 'Параметры конструкторов служб Integration Services: страница "Общие" | Документы Майкрософт'
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Business_Intelligence_Designers.Data_Transformation_Designers.General
ms.assetid: d695690a-923b-4036-945e-7621e8651deb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3651359a836f78c7f962ae571c89d8efc23f574b
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "71286308"
---
# <a name="general-page-of-integration-services-designers-options"></a>Параметры конструкторов служб Integration Services: страница "Общие"

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Страница **Общие** страницы **Конструкторы служб Integration Services** диалогового окна **Параметры** позволяет указать параметры загрузки, отображения и обновления пакетов.  
  
 Чтобы открыть страницу **Общие** , в среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]в меню **Сервис** щелкните **Параметры**, раскройте **Конструкторы бизнес-аналитики**и выберите **Конструкторы служб Integration Services**.  
  
## <a name="options"></a>Параметры  
 **Проверка цифровой подписи при загрузке пакета**  
 Установите этот флажок, чтобы службы [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] проверяли цифровую подпись при загрузке пакета [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] проверяют только наличие цифровой подписи, ее правильность и надежность источника. [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] не проверяют, изменялся ли пакет с момента его подписания.  
  
 Если установлено значение реестра **BlockedSignatureStates** , оно переопределяет параметр **Проверять цифровую подпись при загрузке пакета** . Дополнительные сведения см. в разделе [Реализация политики подписывания путем задания параметра реестра](../integration-services/packages/implement-a-signing-policy-by-setting-a-registry-value.md).  
  
 Дополнительные сведения о цифровых сертификатах и пакетах см. в разделе [Определение источника пакетов с помощью цифровых подписей](../integration-services/security/identify-the-source-of-packages-with-digital-signatures.md).  
  
 **Показывать предупреждение, если пакет не подписан**  
 Выберите этот параметр, чтобы отображать предупреждение при загрузке неподписанного пакета.  
  
 **Отобразить метки элементов управления очередностью**  
 Выберите метку "Успешно", "Ошибка" или "Завершение" для отображения объектов управления очередностью при просмотре пакетов в среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
 **Язык сценария**  
 Выберите значение по умолчанию для языка скрипта новых задач «Скрипт» и компонентов скрипта.  
  
 **Обновить строки соединения для использования новых имен поставщиков**  
 При открытии или обновлении пакетов служб [!INCLUDE[ssISversion2005](../includes/ssisversion2005-md.md)] обновите строки подключения, чтобы использовать в них принятые в текущем выпуске [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]имена следующих поставщиков:  
  
-   [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Поставщик OLE DB  
  
-   Собственный клиент [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]  
  
 Мастер обновления пакетов [!INCLUDE[ssIS](../includes/ssis-md.md)] обновляет только те строки подключения, которые хранятся в диспетчерах соединений. Мастер не обновляет строки соединения, которые формируются динамически с помощью языка выражений служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] или программно в задаче «Скрипт».  
  
 **Создать новый идентификатор пакета**  
 При обновлении пакетов служб [!INCLUDE[ssISversion2005](../includes/ssisversion2005-md.md)] создает новые идентификаторы пакетов для обновленных версий пакетов.  
  
## <a name="see-also"></a>См. также:  
 [Общие сведения о безопасности (службы Integration Services)](../integration-services/security/security-overview-integration-services.md)   
 [Расширение пакетов с помощью сценариев](../integration-services/extending-packages-scripting/extending-packages-with-scripting.md)  
  
  
