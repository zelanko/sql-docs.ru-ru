---
title: Подключение к любому компоненту SQL Server из SQL Server Management Studio | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- connections [SQL Server], SQL Server Management Studio
- saving connections
- components [SQL Server], connections
- SQL Server Management Studio [SQL Server], connections
ms.assetid: 5eeb41bd-b25b-4d3b-a005-a7d9e4b5978e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4dac1363ce1c2f9ec1a82f7bb1b699b0f23240f0
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85058643"
---
# <a name="connect-to-any-sql-server-component-from-sql-server-management-studio"></a>Подключение к любому компоненту сервера SQL Server из среды SQL Server Management Studio
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] содержит функции управления всеми компонентами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Используйте среду [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] для соединения со следующими компонентами и службами:  
  
-   Экземпляр компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
 Хотя [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] позволяет работать с запросами без предварительного установления соединения с источником данных, для большинства других задач такое соединение требуется. [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] предоставляет диалоговое окно **Соединение с сервером** , в котором можно настроить свойства компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . При запуске [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] открывается диалоговое окно **Соединение с сервером** с запросом на подключение к серверу. В диалоговом окне **Соединение с сервером** запоминаются параметры, заданные во время предыдущего его использования.  
  
> [!NOTE]  
>  Эту функцию можно отключить, чтобы отменить автоматическую установку соединения. Дополнительные сведения см. в разделе [Параметры запуска службы Database Engine](../../database-engine/configure-windows/database-engine-service-startup-options.md).  
  
## <a name="saving-connections"></a>сохранение соединений  
 Соединение с конкретными серверами можно сохранять в списке «Зарегистрированные серверы», а также в проектах, создаваемых с помощью обозревателя решений.  
  
### <a name="saving-connections-in-registered-servers"></a>Сохранение соединений в списке «Зарегистрированные серверы»  
 При регистрации сервера среда [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] сохраняет данные соединения к нему в списке «Зарегистрированные серверы». Для соединения с зарегистрированным сервером дважды щелкните имя сервера в списке «Зарегистрированные серверы». После этого соединение с сервером откроется в обозревателе объектов.  
  
### <a name="saving-connections-in-solution-explorer"></a>Сохранение соединений в обозревателе решений  
 Обозреватель решений позволяет хранить связанные запросы, скрипты, соединения, а также другие связанные данные в проекте. Каждый проект скриптов содержит узел **Соединения**, в котором можно сохранить одно или несколько соединений. Для добавления соединения щелкните правой кнопкой мыши узел **Соединения**и выберите **Создать соединение**. Для доступа к сохраненному соединению разверните пункт **Соединения** и дважды щелкните нужное соединение. [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] позволяет открыть окно запроса, связанное с заданным соединением. При сохранении скриптов они остаются связанными с конкретным соединением.  
  
## <a name="see-also"></a>См. также:  
 [Использование SQL Server Management Studio](../sql-server-management-studio-ssms.md)   
 [Обозреватель объектов](../object/object-explorer.md)  
  
  
