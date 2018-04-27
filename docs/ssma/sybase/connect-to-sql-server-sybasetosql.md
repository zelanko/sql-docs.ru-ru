---
title: Подключение к SQL Server (SybaseToSQL) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-sybase
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-ssma
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 30179b25-409b-4e23-bc73-2f226657098f
caps.latest.revision: 3
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 559e3806c738cac6e745baeb1c649662600723f4
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="connect-to-sql-server-sybasetosql"></a>Подключение к SQL Server (SybaseToSQL)
Используйте **подключение к SQL Server** диалоговое окно подключения к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] , необходимо выполнить перенос. Чтобы получить доступ к **подключение к SQL Server** в диалоговом **файл** меню, нажмите кнопку **подключение к SQL Server**.  
  
## <a name="options"></a>Параметры  
**Имя сервера**  
Введите или выберите экземпляр SQL Server для подключения к. По умолчанию отображается экземпляр, который вы подключились к последним.  
  
-   При подключении к экземпляру по умолчанию на локальном компьютере, при вводе любого **localhost** или точку (**.**).  
  
-   При подключении к экземпляру по умолчанию на другом компьютере, введите имя компьютера.  
  
-   При подключении к именованному экземпляру на другом компьютере, введите имя компьютера, обратную косую черту и имя экземпляра, например *MyServer*\\*MyInstance*.  
  
**Порт сервера**  
Если ваш экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] не настроена на прием подключений по умолчанию порт (1433), введите номер порта. В противном случае оставьте это поле пустым.  
  
**База данных**  
Укажите базу данных для переноса объектов и данных. Этот параметр недоступен, если повторное подключение к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
**Проверка подлинности**  
Выберите метод проверки подлинности, используемый для подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Чтобы использовать текущую учетную запись Windows, выберите проверку подлинности Windows. Чтобы указать [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] входа и пароль, выберите [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] проверки подлинности.  
  
**Имя пользователя**  
Если вы используете [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] проверки подлинности, введите имя входа для этого экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Этот параметр недоступен, если используется проверка подлинности Windows.  
  
**Пароль**  
Если вы используете [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] проверки подлинности, введите пароль для входа в систему на этом экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Этот параметр недоступен, если используется проверка подлинности Windows.  
  
**Шифровать соединение**  
Если требуется для безопасного подключения к SQL Server использовать соединения Encrypt, проверив **шифровать соединение** флажок.  
  
**Надежный сертификат сервера**  
Если вы хотите использовать этот параметр, выберите **доверять сертификату сервера** флажок.  
  
> [!NOTE]  
> Чтобы включить **доверять сертификату сервера**, «Шифрование» должно быть присвоено **True**.  
  
