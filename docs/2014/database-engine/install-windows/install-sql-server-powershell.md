---
title: Установка компонентов SQL Server PowerShell | Документы Майкрософт
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 854c0b2f-02d2-46a4-a8cc-6b7a5d191cf8
caps.latest.revision: 6
author: mgblythe
ms.author: mblythe
manager: jhubbard
ms.openlocfilehash: 26ddefde6223effd90d2130c40c28011de411802
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36180332"
---
# <a name="install-sql-server-powershell"></a>Установка компонентов SQL Server PowerShell
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Программа установки будет остановлена, если обнаруживает, что выбрана [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] функциональные возможности, включая компоненты PowerShell, а Windows PowerShell 2.0 не установлена. Необходимо установить PowerShell с помощью Windows Management Framework, а затем повторно запустить программу установки.  
  
## <a name="installing-includessnoversionincludesssnoversion-mdmd-powershell-support"></a>Установка компонентов поддержки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell  
 Выполняется установка программного обеспечения, обеспечивающего поддержку [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для Windows PowerShell, с помощью программы установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . При выборе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддержки функций, требующих PowerShell, программа установки проверяет, что установлен Windows PowerShell 2.0. Если присутствует PowerShell 2.0, то программа установки установит следующие [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] компоненты PowerShell:  
  
-   Оснастки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell. Оснастки представляют собой DLL-файлы, в которых реализованы следующие два типа компонентов поддержки Windows PowerShell для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
    -   Набор командлетов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Командлеты — это команды, выполняющие определенные действия. Например, командлет **Invoke-Sqlcmd** запускает скрипт [!INCLUDE[tsql](../../includes/tsql-md.md)] или XQuery, который также можно выполнить с помощью программы **sqlcmd** , а командлет **Invoke-PolicyEvaluation** сообщает, соответствуют ли объекты [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] схемам управления на основе политик.  
  
    -   Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Поставщик позволяет перемещаться по иерархии объектов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , используя путь, похожий на путь файловой системы. Каждый объект соответствует классу из моделей управляющих объектов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Для работы с объектами можно использовать методы и свойства соответствующего класса. Например, если с помощью команды cd перейти к объекту Databases в пути, можно использовать методы и свойства класса Microsoft.SqlServer.Management.SMO.Database.  
  
-   **Sqlps** , импортируемый в сеансы Windows PowerShell 2.0 для загрузки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] оснастки.  
  
-   Устаревшие **sqlps** служебную программу, которая запускает сеанс Windows PowerShell 2.0 и импортирует **sqlps** модуля.  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] поддерживает запуск сеансов Windows PowerShell из дерева обозревателя объектов. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает шаги заданий Windows PowerShell.  
  
 Если Windows PowerShell 2.0 не установлен или удален, его необходимо установить, следуя указаниям [Windows Management Framework](http://go.microsoft.com/fwlink/?LinkId=186214) страницы.  
  
 Если Windows PowerShell удаляется после завершения установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возможности Windows PowerShell не будет работать. Пользователи Windows могут удалить Windows PowerShell, и, кроме того, удаление Windows PowerShell может быть необходимо для некоторых вариантов обновления ОС Windows. Для использования функций [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell необходимо повторно установить PowerShell 2.0 с помощью Windows Management Framework.  
  
## <a name="see-also"></a>См. также  
 [SQL Server PowerShell](../../powershell/sql-server-powershell.md)  
  
  