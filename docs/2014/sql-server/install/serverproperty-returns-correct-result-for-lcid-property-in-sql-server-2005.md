---
title: В SQL Server 2005 функция SERVERPROPERTY возвращает правильный результат для свойства LCID | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SERVERPROPERTY function
ms.assetid: 833a2fc9-b480-4697-aa7b-9677e78ee0b4
caps.latest.revision: 17
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2b0179ebe39b56082bc51cfe944e6de28e0b4a2c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36191134"
---
# <a name="serverproperty-returns-correct-result-for-lcid-property-in-sql-server-2005"></a>В SQL Server 2005 функция SERVERPROPERTY возвращает правильный результат для свойства LCID
  При выполнении функции SERVERPROPERTY('LCID') на серверах с параметрами двоичной сортировки эта функция возвращает значение LCID, соответствующее параметрам сортировки сервера.  
  
> [!NOTE]  
>  Для пакетных файлов и файлов трассировки, использующих функцию SERVERPROPERTY ('LCID') и запускаемых на других экземплярах [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], помощник по обновлению обнаружит это изменение в поведении, только если параметры сортировки у других экземпляров и текущего экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] совпадают.  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Следует изменить приложения, чтобы они ожидали от функции SERVERPROPERTY('LCID') возвращения кода языка Windows, соответствующего параметрам сортировки сервера.  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления компонента Database Engine](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Помощник по обновлению SQL Server 2014 &#91;new&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
