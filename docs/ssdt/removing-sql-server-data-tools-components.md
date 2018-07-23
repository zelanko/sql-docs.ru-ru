---
title: Удаление компонентов SQL Server Data Tools | Документация Майкрософт
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f8ddb919-661f-4868-8c71-87c96f1f4487
caps.latest.revision: 6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 124b4f4f591966d8dc5294f3150892091f71ba74
ms.sourcegitcommit: 2f07d285824a8982c279f3816b220e61a2d91b06
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/29/2018
ms.locfileid: "37094868"
---
# <a name="removing-sql-server-data-tools-components"></a>Удаление компонентов SQL Server Data Tools
Некоторые компоненты SQL Server Data Tools (SSDT) не удаляются при удалении SSDT или Visual Studio.  
  
Следующие пакеты установщика Windows (MSI) не будут удалены с компьютера при удалении SSDT или Visual Studio. При удалении этих компонентов другие версии Visual Studio могут перейти в неподдерживаемое состояние. Если их необходимо удалить, сделайте это с помощью окна «Установка и удаление программ» в Windows.  
  
-   MicrosoftSQL Server Data Tools (SSDT.msi)  
  
-   MicrosoftSQL Server Data Tools Build Utilities (SSDTBuildUtilities.msi)  
  
-   Обязательные компоненты для SSDT (SSDTDBSvcExternals.msi)  
  
Следующие общие компоненты могут использоваться другими программами и при удалении SSDT сохраняются на компьютере.  
  
-   Платформа приложения уровня данных SQL Server (DACFramework.msi)  
  
-   Управляющие объекты SQL Server (SharedManagementObjects.msi)  
  
-   Языковая служба SQL ServerTransact\-SQL (TSqlLanguageService.msi)  
  
-   Microsoft SQL Server System CLR Types для SQL Server (SQLSysClrTypes.msi)  
  
-   SQL ServerTransact\-SQL ScriptDom (SQLDom.msi)  
  
-   SQL ServerTransact\-SQL Compiler Service (SQLLs.msi)  
  
