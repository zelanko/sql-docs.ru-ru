---
title: Регистрация серверов | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.swb.sqlserverregisteredserver.dhelp
helpviewer_keywords:
- connections [SQL Server], registered servers
- registering servers
- servers [SQL Server], registering
- server management [SQL Server], registering servers
- server registration [SQL Server]
ms.assetid: c2a2513e-fa09-419c-99e7-a12d57c5a0db
caps.latest.revision: 28
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b7d990b38bc36ad5a4a4a17d856bfd770a79be59
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36187937"
---
# <a name="register-servers"></a>Регистрация серверов
  Регистрация сервера в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] позволяет сохранить информацию о подключении сервера для будущих подключений. Есть три способа зарегистрировать сервер в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
1.  Локальные экземпляры [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] автоматически регистрируются во время первого запуска среды [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] после ее установки.  
  
2.  Можно также запустить процесс автоматической регистрации в любое время, чтобы восстановить регистрацию локальных экземпляров сервера.  
  
3.  Наконец, можно зарегистрировать сервер с помощью средства «Зарегистрированные серверы» в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
## <a name="benefits-of-registered-servers"></a>Преимущества зарегистрированных серверов  
 С помощью списка «Зарегистрированные серверы» можно:  
  
-   регистрировать серверы для сохранения данных о соединениях;  
  
-   определять, запущен ли зарегистрированный сервер;  
  
-   легко подключать обозреватель объектов и редактор запросов к зарегистрированному серверу;  
  
-   редактировать и удалять регистрационные данные зарегистрированного сервера;  
  
-   создавать группы серверов;  
  
-   назначать зарегистрированным серверам понятные имена путем задания в поле **Имя зарегистрированного сервера** значения, отличного от имеющегося в списке **Имя сервера** ;  
  
-   создавать подробные описания зарегистрированных серверов;  
  
-   указывать подробные описания групп зарегистрированных серверов;  
  
-   экспортировать группы зарегистрированных серверов;  
  
-   импортировать группы зарегистрированных серверов;  
  
-   просматривать файлы журналов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], находящихся в сети и вне сети.  
  
## <a name="related-tasks"></a>Related Tasks  
 Используйте следующие разделы для начала работы с зарегистрированными серверами.  
  
|**Описание**|**Раздел**|  
|---------------------|---------------|  
|Регистрация экземпляров локального сервера|[Регистрация подключенного сервера (среда SQL Server Management Studio)](register-a-connected-server-sql-server-management-studio.md)|  
|Регистрация сервера|[Создание нового зарегистрированного сервера (среда SQL Server Management Studio)](create-a-new-registered-server-sql-server-management-studio.md)|  
|Просмотр зарегистрированных серверов|[Просмотр зарегистрированных серверов в среде SQL Server Management Studio](view-registered-servers-in-sql-server-management-studio.md)|  
|Удаление зарегистрированного сервера|[Удаление зарегистрированного сервера (среда SQL Server Management Studio)](remove-a-registered-server-sql-server-management-studio.md)|  
|Изменение регистрации сервера|[Изменение регистрационных данных сервера (среда SQL Server Management Studio)](change-a-server-s-registration-sql-server-management-studio.md)|  
|Подключение к зарегистрированному серверу|[Подключение к зарегистрированному серверу (среда SQL Server Management Studio)](connect-to-a-registered-server-sql-server-management-studio.md)|  
|Отключение от зарегистрированного сервера|[Отключение от зарегистрированного сервера (среда SQL Server Management Studio)](disconnect-from-a-registered-server-sql-server-management-studio.md)|  
|Перемещение зарегистрированного сервера или группы серверов|[Перемещение зарегистрированного сервера или зарегистрированной группы серверов (среда SQL Server Management Studio)](move-a-registered-server-or-registered-server-group.md)|  
|Изменение имени зарегистрированного сервера или группы серверов|[Изменение имени зарегистрированного сервера или зарегистрированной группы серверов (среда SQL Server Management Studio)](change-the-name-of-registered-server-or-registered-server-group.md)|  
|Создание или изменение группы серверов|[Создание или изменение группы серверов (среда SQL Server Management Studio)](create-or-edit-a-server-group-sql-server-management-studio.md)|  
|Удалить группу серверов|[Удаление группы серверов (среда SQL Server Management Studio)](remove-a-server-group-sql-server-management-studio.md)|  
|Экспорт сведений о зарегистрированном сервере|[Выполнение экспорта сведений компонента "Зарегистрированные серверы" (среда SQL Server Management Studio)](export-registered-server-information-sql-server-management-studio.md)|  
|Удаление сведений о зарегистрированном сервере|[Импорт сведений компонента "Зарегистрированные серверы" (среда SQL Server Management Studio)](import-registered-server-information-sql-server-management-studio.md)|  
|Создание центрального сервера управления и группы серверов|[Создание центрального сервера управления и группы сервера (среда SQL Server Management Studio)](create-a-central-management-server-and-server-group.md)|  
|Выполнение инструкций на нескольких серверах одновременно|[Выполнение инструкции на нескольких серверах одновременно (среда SQL Server Management Studio)](execute-statements-against-multiple-servers-simultaneously.md)|  
  
## <a name="see-also"></a>См. также  
 [Удаленные серверы](../../database-engine/configure-windows/remote-servers.md)  
  
  