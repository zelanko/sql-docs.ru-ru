---
title: Прочие файлы | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- files [SQL Server Management Studio], miscellaneous
- projects [SQL Server Management Studio], files
- solutions [SQL Server Management Studio], files
- miscellaneous files folder [SQL Server]
ms.assetid: 3c952b0b-8f5f-4d86-9e5d-616c10b9df0d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ecabdec464cb72cf5024feab83e547c95cafd9d6
ms.sourcegitcommit: 08b3de02475314c07a82a88c77926d226098e23f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49119807"
---
# <a name="miscellaneous-files"></a>Прочие файлы
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Файлы, внешние для любого проекта, называются *прочими файлами*. Когда решение открыто, можно открывать и изменять прочие файлы, связанные с проектом. Файл считается прочим файлом, если его расширение не связано с редактором кода проектов. Например, в проекте скриптов [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] файлы с расширением TXT и MDX будут считаться прочими. В проекте многомерных выражений файлы с расширением TXT и SQL будут считаться прочими файлами. Сведения о связывании расширения файла с редактором кода см. в разделе [Практическое руководство. Связывание расширения файла с редактором кода](../../relational-databases/scripting/associate-file-extensions-to-a-code-editor.md).  
  
Возможен ряд случаев, когда может быть полезным добавлять в проект прочие файлы. Например, если существует файл, который не является скриптом, но необходим для разработки решения. Распространенные примеры: примечания и инструкции разработчиков, файлы данных и фрагменты кода.  
  
Прочие файлы обеспечивают гибкость. Например, предположим, что в проекте скриптов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] есть несколько скриптов, создающих таблицы и хранимые процедуры в базе данных. Кроме того, есть несколько файлов данных для таблиц с расширением BCP и инструкции по выполнению сценариев в файле README.TXT. Файлы данных и README можно добавить в проект как прочие файлы, чтобы использовать преимущества системы управления версиями и другие возможности системы проектов.  
  
[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] меню и панели инструментов изменяются в зависимости от формата открытого файла. Например, когда открывается текстовый файл, появляется панель инструментов редактора текстов. Если открывается файл XML-схемы, появляется панель инструментов XML-схемы. При изменении XML-схемы панель инструментов редактора текстов недоступна. При переключении между файлом проекта и прочим файлом все относящиеся к проекту команды и панели инструментов заменяются другими, соответствующими прочему файлу.  
  
## <a name="see-also"></a>См. также:  
[Файлы для управления решениями и проектами](../../ssms/solution/files-that-manage-solutions-and-projects.md)  
[Решения (среда SQL Server Management Studio)](../../ssms/solution/solutions-sql-server-management-studio.md)  
[Проекты (SQL Server Management Studio)](../../ssms/solution/projects-sql-server-management-studio.md)  
  
