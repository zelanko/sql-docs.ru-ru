---
description: Диалоговое окно "Подключение к SQL Server" (OracleToSQL)
title: Подключение к SQL Server (OracleToSQL) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 4ef384ea-5f3e-4f70-ad7c-b62d7b0da628
author: nahk-ivanov
ms.author: alexiva
manager: alexiva
ms.openlocfilehash: 1d97fd4a9aa4c92fe1e6376b4b472519b89e4bc7
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88492423"
---
# <a name="connect-to-sql-server--oracletosql"></a>Диалоговое окно "Подключение к SQL Server" (OracleToSQL)
Используйте диалоговое окно **Подключение к SQL Server** , чтобы подключиться к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , на который требуется выполнить миграцию. Чтобы открыть диалоговое окно **Подключение к SQL Server** , в меню **файл** выберите пункт **подключиться к SQL Server**.  
  
## <a name="options"></a>Параметры  
**Имя сервера**  
Введите или выберите экземпляр SQL Server для подключения. По умолчанию отображается экземпляр, который был подключен к последнему.  
  
-   При подключении к экземпляру по умолчанию на локальном компьютере можно ввести либо **localhost** , либо точку (**.**).  
  
-   При подключении к экземпляру по умолчанию на другом компьютере введите имя компьютера.  
  
-   При подключении к именованному экземпляру на другом компьютере введите имя компьютера, обратную косую черту и имя экземпляра, например *MyServer* \\ *myInstance*.  
  
**Порт сервера**  
Если экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не настроен для приема подключений через порт по умолчанию (1433), введите номер порта. В противном случае оставьте это значение пустым.  
  
**База данных**  
Укажите базу данных для переноса объектов и данных. Этот параметр недоступен при повторном подключении к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
**Аутентификация**  
Выберите метод проверки подлинности, используемый для подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Чтобы использовать текущую учетную запись Windows, выберите Проверка подлинности Windows. Чтобы указать [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имя входа и пароль, выберите [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Проверка подлинности.  
  
**User name**  
Если используется [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Проверка подлинности, введите имя входа для этого экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Если используется проверка подлинности Windows, этот параметр недоступен.  
  
**Пароль**  
Если используется [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Проверка подлинности, введите пароль для имени входа на этом экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Если используется проверка подлинности Windows, этот параметр недоступен.  
  
**Шифровать соединение**  
Если вы хотите безопасно подключаться к SQL Server, используйте шифрование соединения, установив флажок **шифровать подключение** .  
  
**Надежный сертификат сервера**  
Если вы хотите использовать этот параметр, установите флажок **доверять сертификату сервера** .  
  
> [!NOTE]  
> Чтобы включить **доверенный сертификат сервера**, параметру "Encrypt" необходимо присвоить значение **true**.  
  
