---
title: "Переключение базы данных служб Analysis Services между режимами ReadOnly и ReadWrite | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ReadOnly property
- ReadWriteMode command
- operations [Analysis Services - multidimensional data]
ms.assetid: 4eff8181-08dd-4fad-b091-d400fc21a020
caps.latest.revision: 16
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 11eaa65564dcd59442bd8b111c0de009b00e8fd4
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="switch-an-analysis-services-database-between-readonly-and-readwrite-modes"></a>Переключение базы данных служб Analysis Services между режимами ReadOnly и ReadWrite
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Администраторы баз данных могут изменить режим чтения и записи табличной или многомерной базы данных в рамках более масштабных действий по распределению рабочей нагрузки запросов между несколькими серверами, обрабатывающими только запросы.  
  
 Существует несколько способов изменения режима работы базы данных. В этом документе описаны следующие распространенные сценарии:  
  
-   интерактивно с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]  
  
-   программным способом с помощью объектов AMO;  
  
-   с помощью скриптов XMLA или TMSL.  
  
## <a name="switch-the-readwrite-mode-of-a-database-interactively-using-management-studio"></a>Интерактивное изменение режима чтения и записи базы данных с помощью среды Management Studio  
  
1.  В обозревателе объектов щелкните правой кнопкой мыши базу данных и выберите пункт **Свойства**.  
  
     Запишите расположение. Пустое место хранения для базы данных означает, что папка базы данных находится в папке данных сервера.  
  
2.  Щелкните правой кнопкой мыши базу данных и выберите команду **Отсоединить...**  
  
3.  Назначьте пароль отсоединяемой базе данных и нажмите кнопку **ОК** , чтобы выполнить команду отсоединения.  
  
4.  В обозревателе объектов щелкните правой кнопкой мыши папку **Базы данных** и выберите команду **Присоединить…**  
  
5.  В текстовом поле **папка** введите начальное местоположение папки базы данных. Выяснить расположение папки базы данных можно также при помощи кнопки обзора (**…**).  
  
6.  Выберите режим чтения/записи для базы данных.  
  
7.  Введите пароль и нажмите кнопку **ОК** , чтобы выполнить команду присоединения.  
  
## <a name="switch-the-readwrite-mode-to-a-database-programmatically-using-amo"></a>Программное изменение режима чтения и записи базы данных с помощью объектов AMO  
 В приложении на C# вызовите метод `SwitchReadWrite()` , указав необходимые параметры. Скомпилируйте и выполните код для перемещения базы данных.  
  
```  
private void SwitchReadWrite(Server server, string dbName, ReadWriteMode dbReadWriteMode)  
{  
    if (server.Databases.ContainsName(dbName))  
    {  
        Database db;  
        string databaseLocation;  
        db = server.Databases[dbName];  
        databaseLocation = db.DbStorageLocation;  
  
              if (databaseLocation == null)  
            {  
                 string dataDir = server.ServerProperties["DataDir"].Value;  
                 string dataDir = server.ServerProperties["DataDir"].Value;  
                 string dataDir = server.ServerProperties["DataDir"].Value;  
  
    String[] possibleFolders = Directory.GetDirectories(dataDir, string.Concat(dbName,"*"), SearchOption.TopDirectoryOnly);  
  
   if (possibleFolders.Length > 1)  
         {  
         List<String> sortedFolders = new List<string>(possibleFolders.Length);  
         sortedFolders.AddRange(possibleFolders);  
         sortedFolders.Sort();  
         databaseLocation = sortedFolders[sortedFolders.Count - 1];  
         }  
         else  
         {  
         databaseLocation = possibleFolders[0];  
          }  
        }  
    db.Detach();  
    server.Attach(databaseLocation, dbReadWriteMode);  
    }  
}  
  
```  
  
## <a name="switch-the-readwrite-mode-to-a-database-by-script-using-xmla"></a>Изменение режима чтения и записи базы данных с помощью скрипта XMLA  
 Следующие инструкции применяются к многомерным и табличным базам данных в режиме совместимости 1050, 1100 или 1103.  
  
1.  В обозревателе объектов щелкните правой кнопкой мыши базу данных и выберите пункт **Свойства**.  
  
     Запишите расположение. Пустое место хранения для базы данных означает, что папка базы данных находится в папке данных сервера.  
  
2.  Щелкните правой кнопкой мыши базу данных и выберите команду **Отсоединить...**  
  
3.  Откройте новую вкладку XML для аналитики в среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  
  
4.  Скопируйте следующий шаблон скрипта XML для аналитики.  
  
    ```  
    <Detach xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
       <Object>  
          <DatabaseID>%dbName%</DatabaseID>  
          <Password>%password%</Password>  
       </Object>  
    </Detach>  
    ```  
  
5.  Замените шаблон `%dbName%` именем базы данных, а шаблон `%password%` — соответствующим паролем. Символы «%» являются частью шаблона, и поэтому их необходимо удалить.  
  
6.  Выполните команду XML для аналитики.  
  
7.  Скопируйте следующий шаблон скрипта XML для аналитики в новую вкладку XML для аналитики.  
  
    ```  
    <Attach xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
       <Folder>%dbFolder%</Folder>  
       <ReadWriteMode xmlns="http://schemas.microsoft.com/analysisservices/2008/engine/100">%ReadOnlyMode%</ReadWriteMode>  
    </Attach>  
    ```  
  
8.  Замените шаблон `%dbFolder%` полным путем к папке базы данных в формате UNC, шаблон `%ReadOnlyMode%` — соответствующим значением ( **ReadOnly** или **ReadWrite**), а шаблон `%password%` — паролем. Символы «%» являются частью шаблона, и поэтому их необходимо удалить.  
  
9. Выполните команду XML для аналитики.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.AnalysisServices.Database.Detach%2A>   
 [Высокий уровень доступности и масштабируемость в службах Analysis Services](../../analysis-services/instances/high-availability-and-scalability-in-analysis-services.md)   
 [Присоединение и отсоединение баз данных служб Analysis Services](../../analysis-services/multidimensional-models/attach-and-detach-analysis-services-databases.md)   
 [Место хранения базы данных](../../analysis-services/multidimensional-models/database-storage-location.md)   
 [Режимы ReadWriteModes базы данных](../../analysis-services/multidimensional-models/database-readwritemodes.md)   
 [Элемент Attach](../../analysis-services/xmla/xml-elements-commands/attach-element.md)   
 [Элемент detach](../../analysis-services/xmla/xml-elements-commands/detach-element.md)   
 [Элемент ReadWriteMode](../../analysis-services/xmla/xml-elements-properties/readwritemode-element.md)   
 [Элемент DbStorageLocation](../../analysis-services/xmla/xml-elements-properties/dbstoragelocation-element.md)  
  
  

