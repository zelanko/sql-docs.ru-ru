---
title: Прочие файлы | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- files [SQL Server Management Studio], miscellaneous
- projects [SQL Server Management Studio], files
- solutions [SQL Server Management Studio], files
- miscellaneous files folder [SQL Server]
ms.assetid: 3c952b0b-8f5f-4d86-9e5d-616c10b9df0d
caps.latest.revision: 21
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b225697095e7a59f237527d4598d8fb3dfa5d99d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37157335"
---
# <a name="miscellaneous-files"></a>Прочие файлы
  Файлы, внешние для любого проекта, называются *прочими файлами*. Когда решение открыто, можно открывать и изменять прочие файлы, связанные с проектом. Файл считается прочим файлом, если его расширение не связано с редактором кода проектов. Например, в проекте скриптов [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] файлы с расширением TXT и MDX будут считаться прочими. В проекте многомерных выражений файлы с расширением TXT и SQL будут считаться прочими файлами. Связывание расширения файла с редактором кода, см. в разделе [связывание расширения файла с редактором кода](../../relational-databases/scripting/associate-file-extensions-to-a-code-editor.md).  
  
 Возможен ряд случаев, когда может быть полезным добавлять в проект прочие файлы. Например, если существует файл, который не является скриптом, но необходим для разработки решения. Распространенные примеры: примечания и инструкции разработчиков, файлы данных и фрагменты кода.  
  
 Прочие файлы обеспечивают гибкость. Например, предположим, что в проекте скриптов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] есть несколько скриптов, создающих таблицы и хранимые процедуры в базе данных. Кроме того, есть несколько файлов данных для таблиц с расширением BCP и инструкции по выполнению сценариев в файле README.TXT. Файлы данных и README можно добавить в проект как прочие файлы, чтобы использовать преимущества системы управления версиями и другие возможности системы проектов.  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] меню и панели инструментов изменяются в зависимости от формата открытого файла. Например, когда открывается текстовый файл, появляется панель инструментов редактора текстов. Если открывается файл XML-схемы, появляется панель инструментов XML-схемы. При изменении XML-схемы панель инструментов редактора текстов недоступна. При переключении между файлом проекта и прочим файлом все относящиеся к проекту команды и панели инструментов заменяются другими, соответствующими прочему файлу.  
  
## <a name="see-also"></a>См. также  
 [Файлы для управления решениями и проектами](files-that-manage-solutions-and-projects.md)   
 [Решения &#40;SQL Server Management Studio&#41;](solutions-sql-server-management-studio.md)   
 [Проекты (SQL Server Management Studio)](projects-sql-server-management-studio.md)  
  
  
