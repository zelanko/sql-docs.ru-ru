---
title: Установка компонентов SQL Server PowerShell | Документы Майкрософт
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 854c0b2f-02d2-46a4-a8cc-6b7a5d191cf8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: dd603a59a1ddb2ede3d3c779d31f13424342edc2
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84932595"
---
# <a name="install-sql-server-powershell"></a>Установка компонентов SQL Server PowerShell
  Выполнение программы установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] будет остановлено, если обнаружится, что выбраны компоненты [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], включающие компоненты PowerShell, а Windows PowerShell 2.0 не установлен. Необходимо установить PowerShell с помощью Windows Management Framework, а затем повторно запустить программу установки.  
  
## <a name="installing-ssnoversion-powershell-support"></a>Установка компонентов поддержки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell  
 Выполняется установка программного обеспечения, обеспечивающего поддержку [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для Windows PowerShell, с помощью программы установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . При выборе компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], требующих поддержки PowerShell, программа установки проверяет, установлен ли Windows PowerShell 2.0. Если PowerShell 2.0 имеется, то программа установки установит следующие компоненты [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell:  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Оснастки PowerShell. Оснастки представляют собой DLL-файлы, которые реализуют два типа поддержки Windows PowerShell для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
    -   Набор командлетов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Командлеты — это команды, выполняющие определенные действия. Например, командлет **Invoke-Sqlcmd** запускает скрипт [!INCLUDE[tsql](../../includes/tsql-md.md)] или XQuery, который также можно выполнить с помощью программы **sqlcmd** , а командлет **Invoke-PolicyEvaluation** сообщает, соответствуют ли объекты [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] схемам управления на основе политик.  
  
    -   Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Поставщик позволяет перемещаться по иерархии объектов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , используя путь, похожий на путь файловой системы. Каждый объект соответствует классу из моделей управляющих объектов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Для работы с объектами можно использовать методы и свойства соответствующего класса. Например, если с помощью команды cd перейти к объекту Databases в пути, можно использовать методы и свойства класса Microsoft.SqlServer.Management.SMO.Database.  
  
-   Модуль **sqlps** , который импортируется в сеансы Windows PowerShell 2,0 для загрузки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] оснасток.  
  
-   Устаревшая служебная программа **sqlps** , которая запускает сеанс Windows PowerShell 2,0 и импортирует модуль **sqlps** .  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] поддерживает запуск сеансов Windows PowerShell из дерева обозревателя объектов. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает шаги заданий Windows PowerShell.  
  
 Если Windows PowerShell 2,0 не установлена или была удалена, необходимо установить ее, следуя инструкциям на странице [Windows Management Framework](https://go.microsoft.com/fwlink/?LinkId=186214) .  
  
 Если Windows PowerShell удалить после завершения программы установки, то функции [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для Windows PowerShell не будут работать. Пользователи Windows могут удалить Windows PowerShell, и, кроме того, удаление Windows PowerShell может быть необходимо для некоторых вариантов обновления ОС Windows. Для использования функций [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell необходимо повторно установить PowerShell 2.0 с помощью Windows Management Framework.  
  
## <a name="see-also"></a>См. также:  
 [SQL Server PowerShell](../../powershell/sql-server-powershell.md)  
  
  
