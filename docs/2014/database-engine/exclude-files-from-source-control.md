---
title: Исключить файлы из системы управления версиями | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- excluding files from source control
- source controls [SQL Server Management Studio], file exclusions
ms.assetid: 7dcb6514-db5c-49eb-8b5a-2c766ce39aa7
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 9fb3c5ccb4fcaad062236eec6d04f995557dc2b8
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84933095"
---
# <a name="exclude-files-from-source-control"></a>Исключение файлов из системы управления версиями
  Если решение, над которым вы работаете, содержит файлы, которые не нуждаются в службах управления версиями, можно использовать команду **исключить из системы управления версиями** , чтобы исключить файл из системы управления версиями. В этом случае файл остается в базе данных [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe, но его возврат и извлечение в проекте невозможны.  
  
 Следует использовать команду **исключить из системы управления версиями** только для созданных файлов. Созданный файл является файлом, который может быть полностью создан повторно в [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] зависимости от содержимого другого файла в решении.  
  
### <a name="to-exclude-a-file-from-source-control"></a>Исключение файла из управления версиями  
  
1.  В обозревателе решений выберите файл, который необходимо исключить.  
  
2.  В меню **файл** укажите пункт **система управления версиями**, а затем выберите пункт **исключить** *\<file name>* **из системы управления версиями**.  
  
## <a name="see-also"></a>См. также:  
 [Основы системы управления версиями](../../2014/database-engine/source-control-basics.md)   
 [Задание параметров системы управления версиями](../../2014/database-engine/set-source-control-options.md)   
 [Изменение соединений с системой управления версиями](../../2014/database-engine/change-source-control-connections.md)  
  
  
