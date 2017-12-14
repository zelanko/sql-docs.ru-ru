---
title: "Многопользовательские среды (визуальные инструменты для баз данных) | Документация Майкрософт"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: ssms-visual-db
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- users [SQL Server], multiuser environments
- conflict resolution [Visual Database Tools]
- multiple users making database changes
- multiuser environments [Visual Database Tools]
- database modifications [SQL Server]
- version control [Visual Database Tools]
- Visual Database Tools [SQL Server], multiuser environments
ms.assetid: 330bd48c-9427-4967-b58e-b7c492d5ee36
caps.latest.revision: "3"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b698bbf209cc7f30c6b5c13b90104e1cadd752be
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2017
---
# <a name="multiuser-environments-visual-database-tools"></a>Многопользовательские среды (визуальные инструменты для баз данных)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] Многопользовательской называется такая среда, в которой к базе данных, с которой работает пользователь, могут подключаться и другие пользователи, которые, кроме того, могут вносить в нее изменения. В результате с некоторыми объектами базы данных могут работать одновременно несколько пользователей. Таким образом, в многопользовательской среде при внесении изменений в базу данных могут отражаться и изменения, сделанные другими пользователями.  
  
При работе с базами данных в многопользовательской среде основной является проблема прав доступа. Разрешения, которыми обладает пользователь, определяют масштаб действий, который он может выполнять в базе данных. Например, для изменения объектов базы данных нужно иметь соответствующие разрешения на запись. Дополнительные сведения о разрешениях в базе данных см. в документации по базе данных. Дополнительные сведения см. в разделе [Разрешения и визуальные инструменты для баз данных (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/permissions-and-visual-database-tools-visual-database-tools.md).  
  
При сохранении изменений, внесенных в таблицы, конструктор таблиц проверяет наличие изменений в базе данных с момента последнего сохранения пользователем. Если другой пользователь внес изменения, то первый пользователь будет уведомлен об изменениях в базе данных. Возможно, эти изменения потребуется согласовывать. Дополнительные сведения см. в разделе [Согласование изменений, внесенных несколькими пользователями (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/reconcile-changes-made-by-multiple-users-visual-database-tools.md).  
  
Существуют принципы работы в многопользовательской среде, которых следует придерживаться во избежание конфликтов, связанных с изменениями. Дополнительные сведения см. в разделе [Проблемы развития базы данных (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/issues-of-database-evolution-visual-database-tools.md).  
  
Один из способов предотвращения ошибок состоит в том, что изменения вносятся в копию базы данных, например в тестовую базу данных. Затем создается скрипт изменений, который применяет эти изменения к оригиналу после разрешения конфликтов в режиме «вне сети». Дополнительные сведения см. в разделе [Разработка, тестирование и создание баз данных (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/development-test-and-production-databases-visual-database-tools.md).  
  
