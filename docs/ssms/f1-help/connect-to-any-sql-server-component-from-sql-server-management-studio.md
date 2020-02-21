---
title: Подключение к любому компоненту SQL Server
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- connections [SQL Server], SQL Server Management Studio
- saving connections
- components [SQL Server], connections
- SQL Server Management Studio [SQL Server], connections
ms.assetid: 5eeb41bd-b25b-4d3b-a005-a7d9e4b5978e
author: markingmyname
ms.author: maghan
ms.openlocfilehash: ebc0f4a5ca2be46e607ccd8d18399b7fe0ef6814
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "75243929"
---
# <a name="connect-to-any-sql-server-component-from-sql-server-management-studio"></a>Подключение к любому компоненту сервера SQL Server из среды SQL Server Management Studio
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] содержит функции управления всеми компонентами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Используйте среду [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] для соединения со следующими компонентами и службами:  
  
-   Экземпляр компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)].  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion_md.md)].  
  
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
Хотя [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] позволяет работать с запросами без предварительного установления соединения с источником данных, для большинства других задач такое соединение требуется. [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] предоставляет диалоговое окно **Соединение с сервером** , в котором можно настроить свойства компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . При запуске [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] открывается диалоговое окно **Соединение с сервером** с запросом на подключение к серверу. В диалоговом окне **Соединение с сервером** запоминаются параметры, заданные во время предыдущего его использования.  
  
> [!NOTE]  
> Эту функцию можно отключить, чтобы отменить автоматическую установку соединения. Дополнительные сведения см. в разделе [Параметры запуска службы Database Engine](../../database-engine/configure-windows/database-engine-service-startup-options.md).  
  
## <a name="saving-connections"></a>сохранение соединений  
Соединение с конкретными серверами можно сохранять в списке «Зарегистрированные серверы», а также в проектах, создаваемых с помощью обозревателя решений.  
  
### <a name="saving-connections-in-registered-servers"></a>Сохранение соединений в списке «Зарегистрированные серверы»  
При регистрации сервера среда [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] сохраняет данные соединения к нему в списке «Зарегистрированные серверы». Для соединения с зарегистрированным сервером дважды щелкните имя сервера в списке «Зарегистрированные серверы». После этого соединение с сервером откроется в обозревателе объектов.  
  
### <a name="saving-connections-in-solution-explorer"></a>Сохранение соединений в обозревателе решений  
Обозреватель решений позволяет хранить связанные запросы, скрипты, соединения, а также другие связанные данные в проекте. Каждый проект скриптов содержит узел **Соединения**, в котором можно сохранить одно или несколько соединений. Для добавления соединения щелкните правой кнопкой мыши узел **Соединения**и выберите **Создать соединение**. Для доступа к сохраненному соединению разверните пункт **Соединения** и дважды щелкните нужное соединение. [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] позволяет открыть окно запроса, связанное с заданным соединением. При сохранении скриптов они остаются связанными с конкретным соединением.  
  
## <a name="see-also"></a>См. также:  
[Использование среды SQL Server Management Studio](../../ssms/use-sql-server-management-studio.md)  
[Обозреватель объектов](../../ssms/object/object-explorer.md)  
  
