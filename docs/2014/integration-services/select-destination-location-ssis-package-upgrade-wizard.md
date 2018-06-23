---
title: Выбор целевого расположения (мастер обновления пакетов служб SSIS) | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.is.upgradewizard.selectdestinationlocation.f1
ms.assetid: 89274a71-0ffe-4889-84df-f5a7d78459ef
caps.latest.revision: 19
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 01d2788228da6244572a987700e1be64d297e63b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36190768"
---
# <a name="select-destination-location-ssis-package-upgrade-wizard"></a>Выбор целевого расположения (мастер обновления пакетов служб SSIS)
  Страница **Выбор целевого расположения** используется для указания назначения, в которое сохраняются обновленные пакеты.  
  
> [!NOTE]  
>  Эта страница доступна только при запуске мастера обновления пакетов служб [!INCLUDE[ssIS](../includes/ssis-md.md)] в среде [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] или из командной строки.  
  
 **Запуск мастера обновления пакетов служб SSIS**  
  
-   [Обновление пакетов служб Integration Services с помощью мастера обновления пакетов служб SSIS](install-windows/upgrade-integration-services-packages-using-the-ssis-package-upgrade-wizard.md)  
  
## <a name="static-options"></a>Статические параметры  
 **Сохранить в исходное расположение**  
 Сохраните обновленные пакеты в то же расположение, которое было указано на странице мастера **Выбор исходного расположения** .  
  
 Если исходные пакеты хранились в файловой системе и нужно, чтобы мастер создал их резервные копии, выберите параметр **Сохранить в исходное расположение** . Дополнительные сведения см. в разделе [Обновление пакетов служб Integration Services с помощью мастера обновления пакетов служб SSIS](install-windows/upgrade-integration-services-packages-using-the-ssis-package-upgrade-wizard.md).  
  
 **Выбрать новое целевое расположение**  
 Сохраните обновленные пакеты в расположение, указанное на этой странице.  
  
 **Источник пакета**  
 Позволяет указать, где будут храниться обновленные пакеты. Все возможные значения этого параметра приведены в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**Файловая система**|Указывает, что обновленные пакеты должны быть сохранены в папку на локальном компьютере.|  
|**Хранилище пакетов служб SSIS**|Указывает, что обновленные пакеты должны быть сохранены в хранилище пакетов служб Integration Services. Хранилище пакетов представляет собой набор папок в файловой системе, управляемый службами Integration Services. Дополнительные сведения см. в разделе [Управление пакетами (службы SSIS)](service/package-management-ssis-service.md).<br /><br /> При выборе этого значения отображаются соответствующие динамические параметры **Источник пакета** .|  
|**Microsoft SQL Server**|Указывает, что обновленные пакеты должны быть сохранены в существующем экземпляре [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].<br /><br /> При выборе этого значения отображаются соответствующие динамические параметры **Источник пакета** .|  
  
 **Папка**  
 Введите имя папки, чтобы сохранить обновленные пакеты, или нажмите кнопку **Обзор** и укажите папку.  
  
 **Обзор**  
 Укажите папку, в которую будут сохранены обновленные пакеты.  
  
## <a name="package-source-dynamic-options"></a>Динамические параметры источника пакетов  
  
### <a name="package-source--ssis-package-store"></a>Источник пакета = хранилище пакетов служб SSIS  
 **Server**  
 Введите имя сервера, на котором будет сохранен обновленный пакет, или выберите сервер из списка.  
  
### <a name="package-source--microsoft-sql-server"></a>Источник пакета = Microsoft SQL Server  
 **Server**  
 Введите имя сервера, на котором будет сохранен обновленный пакет, или выберите сервер из списка.  
  
 **Использовать проверку подлинности Windows**  
 Выберите использование проверки подлинности Windows для подключения к серверу.  
  
 **Использовать проверку подлинности SQL Server**  
 Выберите использование проверки подлинности [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] для подключения к серверу. Если используется проверка подлинности [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , необходимо ввести имя пользователя и пароль.  
  
 **Имя пользователя**  
 Введите имя пользователя, которое будет использовано, если при подключении к серверу применяется проверка подлинности [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
 **Пароль**  
 Введите пароль, который будет использован, если при подключении к серверу применяется проверка подлинности [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
## <a name="see-also"></a>См. также  
 [Обновление пакетов служб Integration Services](install-windows/upgrade-integration-services-packages.md)  
  
  