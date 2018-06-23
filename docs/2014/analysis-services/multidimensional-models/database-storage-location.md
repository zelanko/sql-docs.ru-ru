---
title: Расположение хранилища базы данных | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- databases [Analysis Services], storage location
ms.assetid: cf88c62e-581e-42f2-846f-a9bf1d7c3292
caps.latest.revision: 18
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 1b7c62d96993f1103a216e378bdf89d7b1cdf4ac
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36195033"
---
# <a name="database-storage-location"></a>Место хранения базы данных
  Часто администратору базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] необходимо расположить определенную базу данных вне папки данных сервера. Обычно это связано с производственной необходимостью (например, чтобы повысить производительность или расширить хранилище). В подобных случаях `DbStorageLocation` базы данных позволяет [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] администратор базы данных, чтобы указать расположение базы данных в локальном устройстве диска или сети.  
  
## <a name="dbstoragelocation-database-property"></a>Свойство DbStorageLocation базы данных  
 `DbStorageLocation` Базы данных указывает папку где [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] создает и управляет ими, все базы данных файлы данных и метаданных. Все файлы метаданных хранятся в `DbStorageLocation` папки, за исключением файла метаданных базы данных, который хранится в папке данных сервера. Существует два важных вопросов, при задании значения `DbStorageLocation` свойства базы данных:  
  
-   `DbStorageLocation` Базы данных должен указывать существующий путь UNC или пустая строка. Пустая строка по умолчанию указывает на папку данных сервера. Если папка не существует, при выполнении команды `Create`, `Attach` или `Alter` возникнет ошибка.  
  
-   `DbStorageLocation` Свойство базы данных не может быть присвоено указывало на папку данных сервера или один из ее вложенных папках. В противном случае при выполнении команды `Create`, `Attach` или `Alter` возникнет ошибка.  
  
> [!IMPORTANT]  
>  При использовании сети хранения данных (SAN), сети на основе iSCSI или локально подключенного диска рекомендуется указывать путь в формате UNC. Указание пути в формате UNC к сетевой папке или любым хранилищам с высокой задержкой сделает установку неподдерживаемой.  
  
### <a name="dbstoragelocation-compared-to-storagelocation"></a>Сравнение свойств DbStorageLocation и StorageLocation  
 Свойство `DbStorageLocation` указывает на папку, в которой находятся все файлы данных и метаданных, относящиеся к базе данных, тогда как свойство `StorageLocation` указывает на папку, в которой находятся одна или несколько секций куба. Свойство `StorageLocation` можно задать независимо от свойства `DbStorageLocation`. Администратор базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] принимает решение исходя из поставленной задачи, и зачастую применение того или иного свойства даст одни и те же результаты.  
  
## <a name="dbstoragelocation-usage"></a>Использование свойства DbStorageLocation  
 `DbStorageLocation` Свойство базы данных используется как часть `Create` команду базы данных `Detach` / `Attach` в последовательности команд базы данных `Backup` / `Restore` последовательность команд базы данных , или в `Synchronize` команды базы данных. Изменение свойства `DbStorageLocation` связано со структурными изменениями объекта базы данных. Это означает, что все метаданные будут созданы повторно, а данные повторно обработаны.  
  
> [!IMPORTANT]  
>  Место хранения базы данных не следует изменять командой `Alter`. Вместо этого рекомендуется использовать последовательность `Detach` / `Attach` команд базы данных (в разделе [перемещение базы данных служб Analysis Services](move-an-analysis-services-database.md), [присоединение и отсоединение базы данных Analysis Services](attach-and-detach-analysis-services-databases.md)).  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.AnalysisServices.Database.DbStorageLocation%2A>   
 [Присоединение и отсоединение баз данных служб Analysis Services](attach-and-detach-analysis-services-databases.md)   
 [Перемещение базы данных служб Analysis Services](move-an-analysis-services-database.md)   
 [Элемент DbStorageLocation](../xmla/xml-elements-properties/dbstoragelocation-element.md)   
 [Создать элемент &#40;XML для Аналитики&#41;](../xmla/xml-elements-commands/create-element-xmla.md)   
 [Элемент Attach](../xmla/xml-elements-commands/attach-element.md)   
 [Элемент Synchronize &#40;XML для Аналитики&#41;](../xmla/xml-elements-commands/synchronize-element-xmla.md)  
  
  