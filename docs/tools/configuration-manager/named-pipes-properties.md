---
title: Свойства именованных каналов | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- pipes [SQL Server]
- listening [SQL Server], pipes
- pipes [SQL Server], listening on pipes
- Named Pipes [SQL Server], listening on pipes
ms.assetid: a5fd5b8e-f889-485b-89e3-d4010ec4c6ec
author: markingmyname
ms.author: maghan
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: c42b3846ce4e2eda1e7aaf40eeb47ea76babf0af
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68010140"
---
# <a name="named-pipes-properties"></a>Свойства именованных каналов
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
  Используйте страницу **Протокол**в диалоговом окне **Свойства именованных каналов** , чтобы просмотреть или изменить именованный канал, который прослушивается [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , во время использования протокола именованных каналов.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должен быть перезапущен, чтобы включить протокол, отключить протокол или изменить именованный канал.  
  
## <a name="options"></a>Параметры  
 **Enabled**  
 Возможные значения: **Да** и **Нет**.  
  
 **Имя канала**  
 Указывает именованный канал, который прослушивается [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . По умолчанию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] прослушивает `\\.\pipe\sql\query` для экземпляра по умолчанию и `\\.\pipe\MSSQL$<instancename>\sql\query` для именованного экземпляра. Длина этого поля ограничена 2047 символами.  
  
## <a name="creating-an-alternate-named-pipe"></a>Создание альтернативного именованного канала  
 Чтобы изменить именованный канал, введите новое имя канала в поле **Имя канала** , а затем остановите и перезапустите [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Так как **sql\query** хорошо известен в качестве именованного канала, используемого [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], изменение канала может помочь сократить риск проведения атак вредоносными программами.  
  
### <a name="example"></a>Пример  
 Введите **\\\\.\pipe\unit\app** , чтобы прослушивать канал **unit\app** .  
  
 Введите **\\\\.\pipe\acct** , чтобы прослушивать канал **acct** .  
  
## <a name="see-also"></a>См. также:  
 [Включение или отключение сетевого протокола сервера](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)   
 [Выбор сетевого протокола](https://msdn.microsoft.com/library/6565fb7d-b076-4447-be90-e10d0dec359a)   
 [Создание допустимой строки подключения, использующей протокол именованных каналов](https://msdn.microsoft.com/library/90930ff2-143b-4651-8ae3-297103600e4f)  
  
  
