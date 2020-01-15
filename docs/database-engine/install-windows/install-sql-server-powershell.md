---
title: Установка компонентов SQL Server PowerShell | Документы Майкрософт
ms.custom: ''
ms.date: 09/05/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 854c0b2f-02d2-46a4-a8cc-6b7a5d191cf8
author: MashaMSFT
ms.author: mathoma
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: f445d1b28c7f76274a2a64e813805f820d005aa6
ms.sourcegitcommit: 381595e990f2294dbf324ef31071e2dd2318b8dd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2019
ms.locfileid: "74200477"
---
# <a name="install-sql-server-powershell"></a>Установка компонентов SQL Server PowerShell
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Программа установки автоматически настраивает компоненты PowerShell.  

Выполняется установка программного обеспечения, обеспечивающего поддержку [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для Windows PowerShell, с помощью программы установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . При выборе компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], требующих поддержки PowerShell, программа установки устанавливает следующие компоненты [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell:  
  
- Оснастки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell. Оснастки представляют собой DLL-файлы, в которых реализованы следующие два типа компонентов поддержки Windows PowerShell для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
  - Набор командлетов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Командлеты — это команды, выполняющие определенные действия. Например, командлет **Invoke-Sqlcmd** запускает скрипт [!INCLUDE[tsql](../../includes/tsql-md.md)] или XQuery, который также можно выполнить с помощью программы **sqlcmd** , а командлет **Invoke-PolicyEvaluation** сообщает, соответствуют ли объекты [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] схемам управления на основе политик.  
  
  - Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Поставщик позволяет перемещаться по иерархии объектов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , используя путь, похожий на путь файловой системы. Каждый объект соответствует классу из моделей управляющих объектов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Для работы с объектами можно использовать методы и свойства соответствующего класса. Например, если с помощью команды cd перейти к объекту Databases в пути, можно использовать методы и свойства класса Microsoft.SqlServer.Management.SMO.Database.  
 
- Модуль **sqlps** , импортируемый в сеанс Windows PowerShell для загрузки оснасток [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
 
- [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] поддерживает запуск сеансов Windows PowerShell из дерева обозревателя объектов. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает шаги заданий Windows PowerShell.  
  
В Windows Server 2012 и более поздних версий, а также в Windows 8 и более поздних версий среда PowerShell устанавливается и настраивается автоматически. Сведения об установке Windows PowerShell см. на странице [Установка Windows PowerShell](https://docs.microsoft.com/powershell/scripting/install/installing-windows-powershell).  

Дополнительные сведения см. в разделе:   

- [SQL Server PowerShell](../../relational-databases/scripting/sql-server-powershell.md)  
  
  
