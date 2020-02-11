---
title: Установка советника по переходу | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- installing Upgrade Advisor
- Setup [Upgrade Advisor]
- Upgrade Advisor [SQL Server], installing
ms.assetid: 1b7d6eca-1df1-47df-bbba-0fc485706a95
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7f70d1cbb879f8fc91e48478fb820b71b51bfd2d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66094315"
---
# <a name="installing-upgrade-advisor"></a>Установка помощника по обновлению
  Место установки помощника по обновлению SQL Server 2014 определяется областью анализа. Помощник по обновлению поддерживает удаленный анализ всех компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , кроме служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Если просмотр экземпляров служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]не производится, помощник по обновлению может быть установлен на любой компьютер, который способен установить соединение с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]и соответствует [Upgrade Advisor Prerequisites](../../../2014/sql-server/install/upgrade-advisor-prerequisites.md). Для просмотра экземпляров служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]следует установить помощник по обновлению на сервер отчетов.  
  
 Чтобы установить помощника по обновлению, запустите файл **SQLUA.msi** . Командная строка позволяет производить установку в автоматическом режиме. Синтаксис и примеры можно посмотреть в статье [Installing Upgrade Advisor from the Command Prompt](../../../2014/sql-server/install/installing-upgrade-advisor-from-the-command-prompt.md) .  
  
 Получить файл SQLUA.msi можно:  
  
-   Из папки **redist** установочного носителя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Как часть [загрузки пакета дополнительных компонентов SQL 2014](https://www.microsoft.com/download/details.aspx?id=42295).  
  
## <a name="uninstalling-upgrade-advisor"></a>Удаление помощника по обновлению  
 Помощник по обновлению может быть удален через средство **Установка и удаление программ**. Синтаксис командной строки также поддерживает удаление.  
  
  
