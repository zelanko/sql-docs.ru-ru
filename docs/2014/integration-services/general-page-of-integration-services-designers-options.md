---
title: Страница "Общие" | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Business_Intelligence_Designers.Data_Transformation_Designers.General
ms.assetid: d695690a-923b-4036-945e-7621e8651deb
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: f27ec0c9fe8078bb11a48114a3d456793271853d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62768290"
---
# <a name="general-page"></a>Страница «Общие»
  Страница **Общие** страницы **Конструкторы служб Integration Services** диалогового окна **Параметры** позволяет указать параметры загрузки, отображения и обновления пакетов.  
  
 Чтобы открыть страницу **Общие** , в среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]в меню **Сервис** щелкните **Параметры**, раскройте **Конструкторы бизнес-аналитики**и выберите **Конструкторы служб Integration Services**.  
  
## <a name="options"></a>Параметры  
 **Проверка цифровой подписи при загрузке пакета**  
 Установите этот флажок, чтобы службы [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] проверяли цифровую подпись при загрузке пакета [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] проверяют только наличие цифровой подписи, ее правильность и надежность источника. [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] не проверяют, изменялся ли пакет с момента его подписания.  
  
 Если установлено значение реестра **BlockedSignatureStates** , оно переопределяет параметр **Проверять цифровую подпись при загрузке пакета** . Дополнительные сведения см. в разделе [Реализация политики подписывания путем задания параметра реестра](implement-a-signing-policy-by-setting-a-registry-value.md).  
  
 Дополнительные сведения о цифровых сертификатах и пакетах см. в разделе [Определение источника пакетов с помощью цифровых подписей](security/identify-the-source-of-packages-with-digital-signatures.md).  
  
 **Показывать предупреждение, если пакет не подписан**  
 Выберите этот параметр, чтобы отображать предупреждение при загрузке неподписанного пакета.  
  
 **Отобразить метки элементов управления очередностью**  
 Выберите метку "Успешно", "Ошибка" или "Завершение" для отображения объектов управления очередностью при просмотре пакетов в среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
 **Язык сценария**  
 Выберите значение по умолчанию для языка скрипта новых задач «Скрипт» и компонентов скрипта.  
  
 **Обновить строки соединения для использования новых имен поставщиков**  
 При открытии или обновлении пакетов служб [!INCLUDE[ssISversion2005](../includes/ssisversion2005-md.md)] обновите строки подключения, чтобы использовать в них принятые в текущем выпуске [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]имена следующих поставщиков:  
  
-   [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Поставщик OLE DB  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Собственный клиент  
  
 Мастер обновления пакетов [!INCLUDE[ssIS](../includes/ssis-md.md)] обновляет только те строки подключения, которые хранятся в диспетчерах соединений. Мастер не обновляет строки соединения, которые формируются динамически с помощью языка выражений служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] или программно в задаче «Скрипт».  
  
 **Создать новый идентификатор пакета**  
 При обновлении пакетов служб [!INCLUDE[ssISversion2005](../includes/ssisversion2005-md.md)] создает новые идентификаторы пакетов для обновленных версий пакетов.  
  
## <a name="see-also"></a>См. также:  
 [Общие сведения о безопасности (службы Integration Services)](security/security-overview-integration-services.md)   
 [Расширение пакетов с помощью сценариев](extending-packages-scripting/extending-packages-with-scripting.md)  
  
  
