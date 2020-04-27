---
title: Выбор исходного расположения (мастер обновления пакетов служб SSIS) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.is.upgradewizard.selectsourcelocation.f1
ms.assetid: 429f146e-edb4-4401-a225-f2c8468971c5
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 1ba348d3a47945bf9bb4f375310c5c92e6be7705
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66055935"
---
# <a name="select-source-location-ssis-package-upgrade-wizard"></a>Выбор расположения источника (мастер обновления пакетов служб SSIS)
  Используйте страницу **Выбор исходного расположения** для задания местонахождения источника обновляемых пакетов.  
  
> [!NOTE]  
>  Эта страница доступна только при запуске мастера обновления пакетов служб [!INCLUDE[ssIS](../includes/ssis-md.md)] в среде [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] или из командной строки.  
  
 **Запуск мастера обновления пакетов служб SSIS**  
  
-   [обновить пакеты служб Integration Services с помощью мастера обновления пакетов служб SSIS](install-windows/upgrade-integration-services-packages-using-the-ssis-package-upgrade-wizard.md)  
  
## <a name="static-options"></a>Статические параметры  
 **Источник пакета**  
 Укажите место хранения, содержащее обновляемые пакеты. Все возможные значения этого параметра приведены в следующей таблице.  
  
|Применение|Описание|  
|-----------|-----------------|  
|**Файловая система**|Указывает, что пакеты, подлежащие обновлению, находятся в папке на локальном компьютере.<br /><br /> Чтобы мастер создавал резервные копии исходных пакетов перед их обновлением, исходные пакеты должны храниться в файловой системе. Дополнительные сведения см. в разделе «Как».|  
|**Хранилище пакетов служб SSIS**|Указывает, что обновляемые пакеты находятся в хранилище пакетов. Хранилище пакетов представляет собой набор папок в файловой системе, управляемый службой Windows служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Дополнительные сведения см. в разделе [Управление пакетами (службы SSIS)](service/package-management-ssis-service.md).<br /><br /> При выборе этого значения отображается соответствующий динамический параметр **Источник пакета** .|  
|**Microsoft SQL Server**|Указывает, что подлежащие обновлению пакеты находятся в существующем экземпляре служб [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].<br /><br /> При выборе этого значения отображается соответствующий динамический параметр **Источник пакета** .|  
  
 **Папка**  
 Введите имя папки, содержащей пакеты, которые необходимо обновить, или нажмите кнопку **Обзор** и укажите папку.  
  
 **Обзор**  
 Перейдите к папке, содержащей пакеты, которые необходимо обновить.  
  
## <a name="package-source-dynamic-options"></a>Динамические параметры источника пакетов  
  
### <a name="package-source--ssis-package-store"></a>Источник пакета = хранилище пакетов служб SSIS  
 **Server**  
 Введите имя сервера, на котором хранятся обновляемые пакеты, или выберите сервер из списка.  
  
### <a name="package-source--microsoft-sql-server"></a>Источник пакета = Microsoft SQL Server  
 **Server**  
 Введите имя сервера, на котором хранятся обновляемые пакеты, или выберите сервер из списка.  
  
 **Использовать проверку подлинности Windows**  
 Выберите использование проверки подлинности Windows для подключения к серверу.  
  
 **Использовать проверку подлинности SQL Server**  
 Выберите использование проверки подлинности [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] для подключения к серверу. Если используется проверка подлинности [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , необходимо ввести имя пользователя и пароль.  
  
 **User name**  
 Введите имя пользователя, которое будет использовано для проверки подлинности [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] при подключении к серверу.  
  
 **Пароль**  
 Введите пароль, который будет использован для проверки подлинности [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] при подключении к серверу.  
  
## <a name="see-also"></a>См. также  
 [Обновление пакетов служб Integration Services](install-windows/upgrade-integration-services-packages.md)  
  
  
