---
title: Переключение базы данных служб Analysis Services между режимами ReadOnly и ReadWrite | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0df164b267043e4784260b30b039ecb58c2c4cc7
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
ms.locfileid: "34026731"
---
# <a name="switch-an-analysis-services-database-between-readonly-and-readwrite-modes"></a>Переключение базы данных служб Analysis Services между режимами ReadOnly и ReadWrite
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
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
  
  
