---
title: Расположение хранилища базы данных | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- databases [Analysis Services], storage location
ms.assetid: cf88c62e-581e-42f2-846f-a9bf1d7c3292
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9c4f46a78941b527b809fd17d7d82946cce1b8af
ms.sourcegitcommit: 7fe14c61083684dc576d88377e32e2fc315b7107
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/26/2018
ms.locfileid: "50148199"
---
# <a name="database-storage-location"></a>Место хранения базы данных
  Часто администратору базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] необходимо расположить определенную базу данных вне папки данных сервера. Обычно это связано с производственной необходимостью (например, чтобы повысить производительность или расширить хранилище). В подобных случаях `DbStorageLocation` базы данных позволяет свойство [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] администратор базы данных, чтобы указать расположение базы данных на локальном или сетевом диске.  
  
## <a name="dbstoragelocation-database-property"></a>Свойство DbStorageLocation базы данных  
 Свойство `DbStorageLocation` базы данных указывает папку, в которой службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] создают и хранят все файлы данных и метаданных, входящие в базу данных. Все файлы метаданных хранятся в папке `DbStorageLocation`, за исключением файла метаданных базы данных, который хранится в папке данных сервера. При изменении свойства `DbStorageLocation` базы данных следует руководствоваться следующими двумя важными соображениями.  
  
-   В свойстве базы данных `DbStorageLocation` должен быть задан путь к существующей папке в формате UNC или пустая строка. Пустая строка по умолчанию указывает на папку данных сервера. Если папка не существует, при выполнении команды `Create`, `Attach` или `Alter` возникнет ошибка.  
  
-   Свойство `DbStorageLocation` базы данных не может указывать на папку данных сервера или любую вложенную в нее папку. В противном случае при выполнении команды `Create`, `Attach` или `Alter` возникнет ошибка.  
  
> [!IMPORTANT]  
>  При использовании сети хранения данных (SAN), сети на основе iSCSI или локально подключенного диска рекомендуется указывать путь в формате UNC. Указание пути в формате UNC к сетевой папке или любым хранилищам с высокой задержкой сделает установку неподдерживаемой.  
  
### <a name="dbstoragelocation-compared-to-storagelocation"></a>Сравнение свойств DbStorageLocation и StorageLocation  
 Свойство `DbStorageLocation` указывает на папку, в которой находятся все файлы данных и метаданных, относящиеся к базе данных, тогда как свойство `StorageLocation` указывает на папку, в которой находятся одна или несколько секций куба. Свойство `StorageLocation` можно задать независимо от свойства `DbStorageLocation`. Администратор базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] принимает решение исходя из поставленной задачи, и зачастую применение того или иного свойства даст одни и те же результаты.  
  
## <a name="dbstoragelocation-usage"></a>Использование свойства DbStorageLocation  
 `DbStorageLocation` Свойство базы данных используется как часть `Create` команду базы данных `Detach` / `Attach` последовательности команд базы данных `Backup` / `Restore` последовательности команд , или в `Synchronize` команды базы данных. Изменение свойства `DbStorageLocation` связано со структурными изменениями объекта базы данных. Это означает, что все метаданные будут созданы повторно, а данные повторно обработаны.  
  
> [!IMPORTANT]  
>  Место хранения базы данных не следует изменять командой `Alter`. Вместо этого рекомендуется использовать последовательность `Detach` / `Attach` команд базы данных (см. в разделе [перемещение базы данных служб Analysis Services](move-an-analysis-services-database.md), [присоединение и отсоединение базы данных Analysis Services](attach-and-detach-analysis-services-databases.md)).  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.AnalysisServices.Database.DbStorageLocation%2A>   
 [Подключение и отключение баз данных служб Analysis Services](attach-and-detach-analysis-services-databases.md)   
 [Перемещение базы данных служб Analysis Services](move-an-analysis-services-database.md)   
 [Элемент DbStorageLocation](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/dbstoragelocation-element)   
 [Элемент Create (XMLA)](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla)   
 [Элемент Attach](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/attach-element)   
 [Элемент Synchronize (XMLA)](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/synchronize-element-xmla)  
  
  
