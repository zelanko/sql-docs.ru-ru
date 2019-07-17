---
title: Подключение к SQL Server (OracleToSQL) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 4ef384ea-5f3e-4f70-ad7c-b62d7b0da628
author: Shamikg
ms.author: Shamikg
manager: shamikg
ms.openlocfilehash: e6e06585ca99305d6825898a98a7dbab31b5b39b
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/16/2019
ms.locfileid: "68266172"
---
# <a name="connect-to-sql-server--oracletosql"></a>Диалоговое окно "Подключение к SQL Server" (OracleToSQL)
Используйте **подключение к SQL Server** диалоговое окно для подключения к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , необходимо выполнить перенос. Для доступа к **подключение к SQL Server** диалоговом окне **файл** меню, щелкните **подключение к SQL Server**.  
  
## <a name="options"></a>Параметры  
**Имя сервера**  
Введите или выберите экземпляр SQL Server для подключения к. По умолчанию отображается экземпляр, который вы подключились к последним.  
  
-   Если вы подключаетесь к экземпляру по умолчанию на локальном компьютере, при вводе любого **localhost** или точку ( **.** ).  
  
-   Если вы подключаетесь к экземпляру по умолчанию на другом компьютере, введите имя компьютера.  
  
-   Если вы подключаетесь к именованному экземпляру на другом компьютере, введите имя компьютера, обратную косую черту и имя экземпляра, например *MyServer*\\*MyInstance*.  
  
**Порт сервера**  
Если экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не настроен на прием подключений по умолчанию порт (1433), введите номер порта. В противном случае оставьте это поле пустым.  
  
**База данных**  
Укажите базу данных для переноса объектов и данных. Этот параметр недоступен при подключении к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
**Authentication**  
Выберите метод проверки подлинности, который используется для подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Для использования текущей учетной записи Windows, выберите проверку подлинности Windows. Чтобы указать [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имя входа и пароль, выберите [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности.  
  
**Имя пользователя**  
Если вы используете [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности, введите имя входа для текущего экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. При использовании проверки подлинности Windows, этот параметр недоступен.  
  
**Пароль**  
Если вы используете [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности, введите пароль для имени входа на этом экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. При использовании проверки подлинности Windows, этот параметр недоступен.  
  
**Шифровать соединение**  
Если вы хотите для безопасного подключения к SQL Server, использовать соединения Encrypt, установив флажок **шифровать соединение** флажок.  
  
**Надежный сертификат сервера**  
Если вы хотите использовать этот параметр, выберите **доверять сертификату сервера** флажок.  
  
> [!NOTE]  
> Чтобы включить **доверять сертификату сервера**, «Зашифровать» должно быть присвоено **True**.  
  
