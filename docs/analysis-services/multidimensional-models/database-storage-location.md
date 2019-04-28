---
title: Расположение хранилища базы данных | Документация Майкрософт
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0544e7e7d552098806d4c3d93751631d03520139
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62714801"
---
# <a name="database-storage-location"></a>Место хранения базы данных
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Часто администратору базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] необходимо расположить определенную базу данных вне папки данных сервера. Обычно это связано с производственной необходимостью (например, чтобы повысить производительность или расширить хранилище). В такой ситуации свойство **DbStorageLocation** базы данных позволяет администратору базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] указать расположение базы данных на локальном или сетевом диске.  
  
## <a name="dbstoragelocation-database-property"></a>Свойство DbStorageLocation базы данных  
 Свойство **DbStorageLocation** базы данных указывает папку, в которой службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] создают и хранят все файлы данных и метаданных, входящие в базу данных. Все файлы метаданных хранятся в папке **DbStorageLocation** , за исключением файла метаданных базы данных, который хранится в папке данных сервера. При изменении свойства **DbStorageLocation** базы данных следует руководствоваться следующими двумя важными соображениями.  
  
-   В свойстве базы данных **DbStorageLocation** должен быть задан путь к существующей папке в формате UNC или пустая строка. Пустая строка по умолчанию указывает на папку данных сервера. Если папка не существует, при выполнении команды **Create**, **Attach**или **Alter** возникнет ошибка.  
  
-   Свойство **DbStorageLocation** базы данных не может указывать на папку данных сервера или любую вложенную в нее папку. В противном случае при выполнении команды **Create**, **Attach**или **Alter** возникнет ошибка.  
  
> [!IMPORTANT]  
>  При использовании сети хранения данных (SAN), сети на основе iSCSI или локально подключенного диска рекомендуется указывать путь в формате UNC. Указание пути в формате UNC к сетевой папке или любым хранилищам с высокой задержкой сделает установку неподдерживаемой.  
  
### <a name="dbstoragelocation-compared-to-storagelocation"></a>Сравнение свойств DbStorageLocation и StorageLocation  
 Свойство**DbStorageLocation** указывает на папку, в которой находятся все файлы данных и метаданных, относящиеся к базе данных, тогда как свойство **StorageLocation** указывает на папку, в которой находятся одна или несколько секций куба. Свойство**StorageLocation** можно задать независимо от свойства **DbStorageLocation**. Администратор базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] принимает решение исходя из поставленной задачи, и зачастую применение того или иного свойства даст одни и те же результаты.  
  
## <a name="dbstoragelocation-usage"></a>Использование свойства DbStorageLocation  
 Свойство **DbStorageLocation** базы данных должно включаться в команду базы данных **Create** в последовательности команд **Detach**/**Attach** , **Backup**/**Restore** или в команде **Synchronize** . Изменение свойства **DbStorageLocation** связано со структурными изменениями объекта базы данных. Это означает, что все метаданные будут созданы повторно, а данные повторно обработаны.  
  
> [!IMPORTANT]  
>  Место хранения базы данных не следует изменять командой **Alter** . Вместо этого рекомендуется пользоваться последовательностью команд базы данных **Detach**/**Attach** (см. разделы [Перемещение базы данных служб Analysis Services](../../analysis-services/multidimensional-models/move-an-analysis-services-database.md), [Подключение и отключение баз данных служб Analysis Services](../../analysis-services/multidimensional-models/attach-and-detach-analysis-services-databases.md)).  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.AnalysisServices.Database.DbStorageLocation%2A>   
 [Подключение и отключение баз данных служб Analysis Services](../../analysis-services/multidimensional-models/attach-and-detach-analysis-services-databases.md)   
 [Перемещение базы данных служб Analysis Services](../../analysis-services/multidimensional-models/move-an-analysis-services-database.md)   
 [Элемент DbStorageLocation](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/dbstoragelocation-element)   
 [Элемент Create (XMLA)](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla)   
 [Элемент Attach](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/attach-element)   
 [Элемент Synchronize (XMLA)](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/synchronize-element-xmla)  
  
  
