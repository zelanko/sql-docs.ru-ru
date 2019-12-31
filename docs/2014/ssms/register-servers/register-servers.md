---
title: Регистрация серверов
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.sqlserverregisteredserver.dhelp
helpviewer_keywords:
- connections [SQL Server], registered servers
- registering servers
- servers [SQL Server], registering
- server management [SQL Server], registering servers
- server registration [SQL Server]
ms.assetid: c2a2513e-fa09-419c-99e7-a12d57c5a0db
author: markingmyname
ms.author: maghan
manager: jroth
ms.openlocfilehash: abc12a642343e2c9bf259142680bf101cebf3e8b
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/19/2019
ms.locfileid: "75241323"
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
  
## <a name="related-tasks"></a>Связанные задачи  
 Используйте следующие разделы для начала работы с зарегистрированными серверами.  
  
|**Описание**|**Раздел**|  
|---------------------|---------------|  
|Регистрация экземпляров локального сервера|[Регистрация &#40;SQL Server Management Studio подключенного сервера&#41;](register-a-connected-server-sql-server-management-studio.md)|  
|Регистрация сервера|[Создать &#40;SQL Server Management Studio зарегистрированного сервера&#41;](create-a-new-registered-server-sql-server-management-studio.md)|  
|Просмотр зарегистрированных серверов|[Просмотр зарегистрированных серверов в среде SQL Server Management Studio](view-registered-servers-in-sql-server-management-studio.md)|  
|Удаление зарегистрированного сервера|[Удаление SQL Server Management Studio &#40;зарегистрированного сервера&#41;](remove-a-registered-server-sql-server-management-studio.md)|  
|Изменение регистрации сервера|[Изменение &#40;регистрации сервера SQL Server Management Studio&#41;](change-a-server-s-registration-sql-server-management-studio.md)|  
|Подключение к зарегистрированному серверу|[Подключение к зарегистрированному серверу &#40;SQL Server Management Studio&#41;](connect-to-a-registered-server-sql-server-management-studio.md)|  
|Отключение от зарегистрированного сервера|[Отключение от зарегистрированного сервера &#40;SQL Server Management Studio&#41;](disconnect-from-a-registered-server-sql-server-management-studio.md)|  
|Перемещение зарегистрированного сервера или группы серверов|[Перемещение &#40;SQL Server Management Studio зарегистрированного сервера или зарегистрированной группы серверов&#41;](move-a-registered-server-or-registered-server-group.md)|  
|Изменение имени зарегистрированного сервера или группы серверов|[Измените имя зарегистрированного сервера или зарегистрированной группы серверов &#40;SQL Server Management Studio&#41;](change-the-name-of-registered-server-or-registered-server-group.md)|  
|Создание или изменение группы серверов|[Создание или изменение группы серверов &#40;SQL Server Management Studio&#41;](create-or-edit-a-server-group-sql-server-management-studio.md)|  
|Удалить группу серверов|[Удаление группы серверов &#40;SQL Server Management Studio&#41;](remove-a-server-group-sql-server-management-studio.md)|  
|Экспорт сведений о зарегистрированном сервере|[Экспорт сведений о зарегистрированном сервере &#40;SQL Server Management Studio&#41;](export-registered-server-information-sql-server-management-studio.md)|  
|Удаление сведений о зарегистрированном сервере|[Импорт сведений о зарегистрированном сервере &#40;SQL Server Management Studio&#41;](import-registered-server-information-sql-server-management-studio.md)|  
|Создание центрального сервера управления и группы серверов|[Создание сервера централизованного управления и группы серверов &#40;SQL Server Management Studio&#41;](create-a-central-management-server-and-server-group.md)|  
|Выполнение инструкций на нескольких серверах одновременно|[Выполните инструкции на нескольких серверах одновременно &#40;SQL Server Management Studio&#41;](execute-statements-against-multiple-servers-simultaneously.md)|  
  
## <a name="see-also"></a>См. также  
 [Удаленные серверы](../../database-engine/configure-windows/remote-servers.md)  
  
  
