---
title: Просмотр журнала приложений Windows (Windows) | Документы Майкрософт
ms.custom: ''
ms.date: 02/01/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- viewing logs
- application logs [SQL Server]
- logs [SQL Server], application
- monitoring Windows NT application log [SQL Server]
- Windows NT application logs [SQL Server]
- displaying logs
- monitoring [SQL Server], events
- logs [SQL Server], viewing
ms.assetid: 168a6c6e-12df-46a9-9904-55d63ca8fe14
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: 2e6e721948c2e875a5f9d6e100cdb29f928b4042
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85655268"
---
# <a name="view-the-windows-application-log-windows-10"></a>Просмотр журнала приложений Windows (Windows 10)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Когда для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] настроено использование журнала приложений Windows, каждый сеанс [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] записывает новые события в этот журнал. В отличие от журнала ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , новый журнал приложений не создается заново каждый раз при запуске экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="view-the-windows-application-log"></a>Просмотр журнала приложений Windows  
  
1. На **панели поиска** введите **средство просмотра событий**, а затем выберите классическое приложение **Просмотр событий**.
  
2. В **средстве просмотра событий** откройте **журналы приложений и служб**.

3. События [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] идентифицируются записью **MSSQLSERVER** в столбце **Источник** (именованные экземпляры обозначаются как **MSSQL$** _<имя_экземпляра>_ ). События агента SQL Server идентифицируются записью SQLSERVERAGENT (для именованных экземпляров сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] события агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] идентифицируются при помощи **SQLAgent$** \<*instance_name*>). События службы Microsoft Search идентифицируются записью **Microsoft Search**.  
  
4. Чтобы просмотреть журнал с другого компьютера, щелкните правой кнопкой мыши элемент **Просмотр событий (локальных)** . Выберите пункт **Подключение к другому компьютеру** и заполните поля в диалоговом окне **Выбор компьютера**.  
  
5. Чтобы отображались только события [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], в меню **Вид** выберите пункт **Фильтр**. В списке **Источник событий** выберите **MSSQLSERVER**. Чтобы просмотреть только события агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , в списке **Источник события** вместо этого выберите **SQLSERVERAGENT** .  
  
6. Чтобы просмотреть дополнительные сведения о событии, дважды щелкните событие.  
  
## <a name="see-also"></a>См. также раздел  
 [Просмотр журнала ошибок SQL Server (среда SQL Server Management Studio)](../../relational-databases/performance/view-the-sql-server-error-log-sql-server-management-studio.md)  
  
  
