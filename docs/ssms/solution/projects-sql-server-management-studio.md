---
title: "Проекты (среда SQL Server Management Studio) | Документация Майкрософт"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c13af859-ca66-4e43-b76a-0650ac6566c0
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: e207a41546270197fa35cccd63348107db2d30f4
ms.contentlocale: ru-ru
ms.lasthandoff: 08/18/2017

---
# <a name="projects-sql-server-management-studio"></a>Проекты (среда SQL Server Management Studio)
Проект [!INCLUDE[ssManStudio](../../includes/ssmanstudio_md.md)] представляет собой коллекцию логически связанных скриптов и файлов, которые можно хранить вместе для администрирования и разработки базы данных.  
  
## <a name="script-project-overview"></a>Обзор проекта скрипта  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] отображаются в обозревателе решений среды [!INCLUDE[ssManStudio](../../includes/ssmanstudio_md.md)]. Проект скрипта может содержать 0 или более файлов проекта. В решение можно добавить один проект или объединить в одном решении несколько проектов.  
  
Проекты могут включать следующее:  
  
-   **Соединения**. Соединение, постоянное в пределах проекта, содержит сведения об имени входа, имени сервера, базе данных по умолчанию, предпочитаемом протоколе, типе проверки подлинности и свойствах соединения. Сведения о соединении могут при необходимости храниться вместе со скриптом (см. далее).  
  
-   **Скрипты SQL**. Часто используемые скрипты SQL для пользователя. Двойной щелчок по SQL-файлу в проекте откроет выбранный скрипт в редакторе SQL.  
  
-   **Скрипты многомерных выражений, расширений интеллектуального анализа данных и XML для аналитики**. Часто используемые скрипты многомерных выражений для пользователя. Двойной щелчок по MDX-файлу в проекте откроет выбранный скрипт в редакторе.  
  
-   **Прочие**. Эту папку можно использовать для файлов, которые не подходят по типу к другим узлам, заданным по умолчанию, таким как текстовый файл, содержащий цели проекта.  
  
Проекты также могут интегрироваться в системы управления исходным кодом.  
  
## <a name="connecting-to-an-instance-of-sql-server-from-a-script-project"></a>Подключение к экземпляру SQL Server из проекта скриптов  
Проект скриптов может содержать соединения с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Чтобы подключиться к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] в проекте, нужно щелкнуть соединение. Откроется окно скрипта SQL, которое подключено к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] , указанному в выбранном соединении. Если открыть [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или скрипт многомерных выражений при помощи соединения, в котором используется проверка подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] , то после запуска редактора и загрузки скрипта будет предложено ввести пароль в диалоговом окне **Подключение к SQL Server** .  
  
Соединение закрывается, как только закроется соответствующее окно.  
  
Чтобы изменить сведения о соединении, используйте окно свойств в [!INCLUDE[ssManStudio](../../includes/ssmanstudio_md.md)].  
  
## <a name="project-tasks"></a>Задачи проекта  
  
|Описание задачи|Раздел|  
|--------------------|---------|  
|Описано создание нового проекта в решении.|[Создание проекта](../../ssms/solution/create-a-project.md)|  
|Описано добавление существующего проекта к решению.|[Добавление к решению существующий проект](../../ssms/solution/add-an-existing-project-to-a-solution.md)|  
|Описано изменение места сохранения файлов проекта по умолчанию.|[Изменение местоположения проектов по умолчанию](../../ssms/solution/change-the-default-location-for-projects.md)|  
|Описан просмотр текущих свойств проекта.|[Просмотр свойств проекта](../../ssms/solution/view-project-properties.md)|  
|Описано добавление новых элементов в проект (соединений, файлов скриптов и т. д).|[Добавление в проект новые элементы](../../ssms/solution/add-new-items-to-a-project.md)|  
|Описано создание сведений о подключении для запроса.|[Связь запроса с соединением в проекте](../../ssms/solution/associate-a-query-with-a-connection-in-a-project.md)|  
|Описано изменение сведений о подключении для запроса.|[Изменение соединение, связанное с запросом](../../ssms/solution/change-the-connection-associated-with-a-query.md)|  
|Описано изменение свойств подключения.|[Просмотр или изменение свойств соединения в проекте](../../ssms/solution/view-or-change-the-properties-of-a-connection-in-a-project.md)|  
  
## <a name="see-also"></a>См. также:  
[Обозреватель решений](../../ssms/solution/solution-explorer.md)  
[Решения (среда SQL Server Management Studio)](../../ssms/solution/solutions-sql-server-management-studio.md)  
[Обозреватель решений системы управления версиями](https://msdn.microsoft.com/en-us/library/ms173879.aspx)  
  

