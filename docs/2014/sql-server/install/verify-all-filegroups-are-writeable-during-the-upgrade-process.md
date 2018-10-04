---
title: Проверьте все файловые группы доступны для записи в процессе обновления | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- filegroups [SQL Server], writeable
- writeable filegroups [SQL Server]
ms.assetid: 2985efc1-4b14-46c3-abbd-a656b159f23c
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: cc80c3729e905d11284437f35af50cd4959e3ba0
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48051942"
---
# <a name="verify-all-filegroups-are-writeable-during-the-upgrade-process"></a>Убедитесь, что все файловые группы доступны для записи во время процесса обновления
  Помощник по обновлению обнаружил базу данных, содержащую одну или несколько файловых групп, доступных только для чтения. Все базы данных в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должны содержать файловые группы, доступные для чтения и записи, до начала обновления.  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Действие по исправлению  
 С помощью инструкции ALTER DATABASE переведите файловые группы в режим READ_WRITE.  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления компонента Database Engine](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Помощник по обновлению SQL Server 2014 &#91;new&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
