---
title: Переименование журнала ошибок агента SQL Server (среда SQL Server Management Studio) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- logs [SQL Server], SQL Server Agent
- renaming SQL Server Agent error log
- SQL Server Agent, errors
- errors [SQL Server Agent]
ms.assetid: dee2b199-48af-44cb-9177-d029a5edb169
caps.latest.revision: 27
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: cb195793732393788f698b2e8dca904bf1e5e8ab
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36187943"
---
# <a name="rename-a-sql-server-agent-error-log-sql-server-management-studio"></a>переименовать журнал ошибок агента SQL Server (среда SQL Server Management Studio)
  В этом разделе описано, как переименовать файл, в котором содержится журнал ошибок агента [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [безопасность](#Security)  
  
-   [Переименование журнала ошибок агента SQL Server с помощью среды SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   Узел агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] отображается в обозревателе объектов только при наличии у пользователя разрешения на использование узла.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] будет записывать сведения в новый файл журнала только после перезапуска службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Для выполнения своих функций агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должен быть настроен на использование учетных данных записи, которая является членом предопределенной роли сервера **sysadmin** в среде [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Эта учетная запись должна иметь следующие разрешения Windows.  
  
-   Вход в систему в качестве службы (SeServiceLogonRight)  
  
-   Замена токена уровня процесса (SeAssignPrimaryTokenPrivilege)  
  
-   Обход проходной проверки (SeChangeNotifyPrivilege)  
  
-   Назначение квот памяти процессам (SeIncreaseQuotaPrivilege)  
  
 Дополнительные сведения о разрешениях Windows, необходимых для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] учетная запись службы агента. в разделе [выберите учетную запись для службы агента SQL Server](select-an-account-for-the-sql-server-agent-service.md) и [Настройка учетных записей службы Windows и Разрешения](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-rename-a-sql-server-agent-error-log"></a>Переименование журнала ошибок агента SQL Server  
  
1.  В **обозревателе объектов**щелкните значок «плюс», чтобы развернуть сервер, содержащий журнал агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , который необходимо переименовать.  
  
2.  Щелкните знак "плюс", чтобы развернуть **Агент SQL Server**.  
  
3.  Щелкните правой кнопкой мыши папку **Журналы ошибок** и выберите **Настроить**.  
  
4.  В диалоговом окне **Настройка журналов ошибок агента SQL Server** введите путь к новому файлу и имя файла журнала ошибок в поле **Файл журнала ошибок** . Можно также щелкнуть многоточие **(...)** и открыть диалоговое окно **Укажите расположение журнала ошибок агента** .  
  
5.  После завершения нажмите кнопку **ОК**.  
  
  