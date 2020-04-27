---
title: Переключение базы данных Analysis Services между режимами ReadOnly и ReadWrite | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- ReadOnly property
- ReadWriteMode command
- operations [Analysis Services - multidimensional data]
ms.assetid: 4eff8181-08dd-4fad-b091-d400fc21a020
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 790e509dd29e388dfb697ba577958395a4a046ea
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66072887"
---
# <a name="switch-an-analysis-services-database-between-readonly-and-readwrite-modes"></a>Переключение базы данных служб Analysis Services между режимами ReadOnly и ReadWrite
  Часто возникают ситуации, когда администратору баз данных (dba) служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] необходимо изменить режим чтения/записи в табличной или многомерной базе данных. Эти ситуации часто определяются бизнес-потребностями, например, совместное использование базы данных между пулом [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] серверов для повышения удобства работы пользователей.  
  
 Существует много способов изменения режима работы базы данных. В этом документе описаны следующие распространенные сценарии:  
  
-   интерактивно с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]  
  
-   программным способом с помощью объектов AMO;  
  
-   с помощью скриптов, используя XML для аналитики  
  
## <a name="procedures"></a>Процедуры  
  
#### <a name="to-switch-the-readwrite-mode-of-a-database-interactively-using-management-studio"></a>Интерактивное изменение режима чтения-записи базы данных с помощью среды Management Studio  
  
1.  Найдите на левой или правой панели среды [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] базу данных для переключения.  
  
2.  Щелкните правой кнопкой мыши базу данных и выберите пункт **Свойства**. Найдите папку с базой данных и запишите ее расположение. Пустое место хранения для базы данных означает, что папка базы данных находится в папке данных сервера.  
  
    > [!IMPORTANT]  
    >  После отсоединения базы данных ее расположение будет невозможно определить при помощи среды [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  
  
3.  Щелкните правой кнопкой мыши базу данных и выберите пункт **отсоединить...**  
  
4.  Назначьте пароль отсоединяемой базе данных и нажмите кнопку **ОК** , чтобы выполнить команду отсоединения.  
  
5.  Откройте папку **базы данных** в левой или правой области окна [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  
  
6.  Щелкните правой кнопкой мыши папку **базы данных** и выберите команду **Присоединить...**  
  
7.  В текстовом поле **папка** введите начальное местоположение папки базы данных. Кроме того, можно нажать кнопку обзора (**...**), чтобы найти папку базы данных.  
  
8.  Выберите режим чтения/записи для базы данных.  
  
9. Введите пароль, который использовался на шаге 3, и нажмите кнопку **ОК** , чтобы выполнить команду Attach.  
  
#### <a name="to-switch-the-readwrite-mode-to-a-database-programmatically-using-amo"></a>Программное изменение режима чтения/записи базы данных с помощью объектов AMO  
  
1.  В приложении на C# проведите адаптацию следующего образца кода и выполните указанные задачи.  
  
 `private void SwitchReadWrite(Server server, string dbName,`  
  
 `ReadWriteMode dbReadWriteMode)`  
  
 `{`  
  
 `if (server.Databases.ContainsName(dbName))`  
  
 `{`  
  
 `Database db;`  
  
 `string databaseLocation;`  
  
 `db = server.Databases[dbName];`  
  
 `databaseLocation = db.DbStorageLocation;`  
  
 `if (databaseLocation == null)`  
  
 `{`  
  
 `string dataDir = server.ServerProperties["DataDir"].Value;`  
  
 `String[] possibleFolders = Directory.GetDirectories(dataDir, string.Concat(dbName,"*"), SearchOption.TopDirectoryOnly);`  
  
 `if (possibleFolders.Length > 1)`  
  
 `{`  
  
 `List<String> sortedFolders = new List<string>(possibleFolders.Length);`  
  
 `sortedFolders.AddRange(possibleFolders);`  
  
 `sortedFolders.Sort();`  
  
 `databaseLocation = sortedFolders[sortedFolders.Count - 1];`  
  
 `}`  
  
 `else`  
  
 `{`  
  
 `databaseLocation = possibleFolders[0];`  
  
 `}`  
  
 `}`  
  
 `db.Detach();`  
  
 `server.Attach(databaseLocation, dbReadWriteMode);`  
  
 `}`  
  
 `}`  
  
1.  В приложении на C# вызовите метод `SwitchReadWrite()` , указав необходимые параметры.  
  
2.  Скомпилируйте и выполните код для перемещения базы данных.  
  
#### <a name="to-switch-the-readwrite-mode-to-a-database-by-script-using-xmla"></a>Изменение режима чтения/записи базы данных с помощью скрипта XML для аналитики  
  
1.  Найдите на левой или правой панели среды [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] базу данных для переключения.  
  
2.  Щелкните правой кнопкой мыши базу данных и выберите пункт **Свойства**. Найдите папку с базой данных и запишите ее расположение. Пустое место хранения для базы данных означает, что папка базы данных находится в папке данных сервера.  
  
    > [!IMPORTANT]  
    >  После отсоединения базы данных ее расположение будет невозможно определить при помощи среды [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  
  
3.  Откройте новую вкладку XML для аналитики в среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  
  
4.  Скопируйте следующий шаблон скрипта XML для аналитики.  
  
 `<Detach xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">`  
  
 `<Object>`  
  
 `<DatabaseID>%dbName%</DatabaseID>`  
  
 `<Password>%password%</Password>`  
  
 `</Object>`  
  
 `</Detach>`  
  
1.  Замените шаблон `%dbName%` именем базы данных, а шаблон `%password%` — соответствующим паролем. Символы «%» являются частью шаблона, и поэтому их необходимо удалить.  
  
2.  Выполните команду XML для аналитики.  
  
3.  Скопируйте следующий шаблон скрипта XML для аналитики в новую вкладку XML для аналитики.  
  
 `<Attach xmlns="https://schemas.microsoft.com/analysisservices/2003` `/engine` `">`  
  
 `<Folder>%dbFolder%</Folder>`  
  
 `<ReadWriteMode xmlns="https://schemas.microsoft.com/analysisservices/2008/engine/100">%ReadOnlyMode%</ReadWriteMode>`  
  
 `</Attach>`  
  
1.  Замените шаблон `%dbFolder%` полным путем к папке базы данных в формате UNC, шаблон `%ReadOnlyMode%` — соответствующим значением (`ReadOnly` или `ReadWrite`), а шаблон `%password%` — паролем. Символы «%» являются частью шаблона, и поэтому их необходимо удалить.  
  
2.  Выполните команду XML для аналитики.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.AnalysisServices.Server.Attach%2A>   
 <xref:Microsoft.AnalysisServices.Database.Detach%2A>   
 [Присоединение и отсоединение баз данных Analysis Services](attach-and-detach-analysis-services-databases.md)   
 [Место хранения базы данных](database-storage-location.md)   
 [Режимы readwritemodes базы данных](database-readwritemodes.md)   
 [Элемент Attach](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/attach-element)   
 [Detach, элемент](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/detach-element)   
 [ReadWriteMode, элемент](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/readwritemode-element)   
 [Элемент DbStorageLocation](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/dbstoragelocation-element)  
  
  
