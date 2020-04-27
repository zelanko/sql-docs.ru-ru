---
title: Место хранения базы данных | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- databases [Analysis Services], storage location
ms.assetid: cf88c62e-581e-42f2-846f-a9bf1d7c3292
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2dd3659aed11e4e1cee791fcb5e541471320c82a
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66075901"
---
# <a name="database-storage-location"></a>Место хранения базы данных
  Часто администратору базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] необходимо расположить определенную базу данных вне папки данных сервера. Обычно это связано с производственной необходимостью (например, чтобы повысить производительность или расширить хранилище). В `DbStorageLocation` этих ситуациях свойство Database позволяет [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] администратору базы данных указать расположение базы на локальном диске или сетевом устройстве.  
  
## <a name="dbstoragelocation-database-property"></a>Свойство DbStorageLocation базы данных  
 Свойство `DbStorageLocation` базы данных указывает папку, в которой службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] создают и хранят все файлы данных и метаданных, входящие в базу данных. Все файлы метаданных хранятся в папке `DbStorageLocation`, за исключением файла метаданных базы данных, который хранится в папке данных сервера. При изменении свойства `DbStorageLocation` базы данных следует руководствоваться следующими двумя важными соображениями.  
  
-   В свойстве базы данных `DbStorageLocation` должен быть задан путь к существующей папке в формате UNC или пустая строка. Пустая строка по умолчанию указывает на папку данных сервера. Если папка не существует, при выполнении команды `Create`, `Attach` или `Alter` возникнет ошибка.  
  
-   Свойство `DbStorageLocation` базы данных не может указывать на папку данных сервера или любую вложенную в нее папку. В противном случае при выполнении команды `Create`, `Attach` или `Alter` возникнет ошибка.  
  
> [!IMPORTANT]  
>  При использовании сети хранения данных (SAN), сети на основе iSCSI или локально подключенного диска рекомендуется указывать путь в формате UNC. Указание пути в формате UNC к сетевой папке или любым хранилищам с высокой задержкой сделает установку неподдерживаемой.  
  
### <a name="dbstoragelocation-compared-to-storagelocation"></a>Сравнение свойств DbStorageLocation и StorageLocation  
 Свойство `DbStorageLocation` указывает на папку, в которой находятся все файлы данных и метаданных, относящиеся к базе данных, тогда как свойство `StorageLocation` указывает на папку, в которой находятся одна или несколько секций куба. Свойство `StorageLocation` можно задать независимо от свойства `DbStorageLocation`. Администратор базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] принимает решение исходя из поставленной задачи, и зачастую применение того или иного свойства даст одни и те же результаты.  
  
## <a name="dbstoragelocation-usage"></a>Использование свойства DbStorageLocation  
 Свойство `DbStorageLocation` базы данных используется как `Create` часть команды базы данных в `Detach` / `Attach` последовательности команд базы данных, в `Backup` / `Restore` последовательности команд базы данных или в команде `Synchronize` базы данных. Изменение свойства `DbStorageLocation` связано со структурными изменениями объекта базы данных. Это означает, что все метаданные будут созданы повторно, а данные повторно обработаны.  
  
> [!IMPORTANT]  
>  Место хранения базы данных не следует изменять командой `Alter`. Вместо этого рекомендуется использовать последовательность `Detach` / `Attach` команд базы данных (см. раздел [Перемещение базы данных Analysis Services](move-an-analysis-services-database.md), [Присоединение и отсоединение Analysis Services баз данных](attach-and-detach-analysis-services-databases.md)).  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.AnalysisServices.Database.DbStorageLocation%2A>   
 [Присоединение и отсоединение баз данных Analysis Services](attach-and-detach-analysis-services-databases.md)   
 [Перемещение базы данных Analysis Services](move-an-analysis-services-database.md)   
 [DbStorageLocation, элемент](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/dbstoragelocation-element)   
 [Создание элемента &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla)   
 [Элемент Attach](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/attach-element)   
 [Элемент Synchronize (XMLA)](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/synchronize-element-xmla)  
  
  
