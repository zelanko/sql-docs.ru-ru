---
title: Проверьте все файловые группы доступны для записи в процессе обновления | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- filegroups [SQL Server], writeable
- writeable filegroups [SQL Server]
ms.assetid: 2985efc1-4b14-46c3-abbd-a656b159f23c
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 758207977c8ddf92d6696dda71a8943e6a596d4d
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66091188"
---
# <a name="verify-all-filegroups-are-writeable-during-the-upgrade-process"></a>Убедитесь, что все файловые группы доступны для записи во время процесса обновления
  Помощник по обновлению обнаружил базу данных, содержащую одну или несколько файловых групп, доступных только для чтения. Все базы данных в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должны содержать файловые группы, доступные для чтения и записи, до начала обновления.  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Действие по исправлению  
 С помощью инструкции ALTER DATABASE переведите файловые группы в режим READ_WRITE.  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления компонента Database Engine](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Помощник по обновлению SQL Server 2014 &#91;new&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
