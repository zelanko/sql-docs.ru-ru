---
title: Получение данных из модели интеллектуального анализа данных (расширения интеллектуального анализа данных) | Документация Майкрософт
description: Сведения о том, как использовать данные из модели интеллектуального анализа данных SQL Server Analysis Services (SSAS) в отчете.
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-data
ms.topic: conceptual
helpviewer_keywords:
- retrieving report data
- datasets [Reporting Services], with DMX queries
- datasets [Reporting Services], Analysis Services
- queries [Reporting Services], data mining prediction
ms.assetid: d9cd3624-1594-4707-8887-55437dd7e07c
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 8e8e6d382e1041e4b15b089d3d6f0ef2a2bfbf6c
ms.sourcegitcommit: 783b35f6478006d654491cb52f6edf108acf2482
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/09/2020
ms.locfileid: "91890833"
---
# <a name="retrieve-data-from-a-data-mining-model-dmx-ssrs"></a>Получение данных из модели интеллектуального анализа данных (расширения интеллектуального анализа данных) (службы SSRS)
  Для использования в отчете данных из модели интеллектуального анализа данных служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] необходимо определить источник данных служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] и один или несколько наборов данных отчета. При создании определения источника данных необходимо указать строку соединения и учетные данные, необходимые для осуществления доступа к источнику данных с компьютера клиента.  
  
 Можно создать определение внедренного источника данных для использования в одном отчете или определение общего источника данных для использования в нескольких отчетах. Процедуры в этом разделе предназначены для создания внедренного источника данных. Дополнительные сведения об общих источниках данных см. в разделах [Внедренные и общие подключения к данным или источники данных (построитель отчетов и службы SSRS)](./data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md) и [Создание, изменение и удаление общих источников данных (SSRS)](../../reporting-services/report-data/create-modify-and-delete-shared-data-sources-ssrs.md).  
  
 После определения источника данных служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] можно создать один или несколько наборов данных. Для каждого из наборов данных следует использовать конструктор запросов прогноза интеллектуального анализа данных (расширения интеллектуального анализа данных), чтобы создать DMX-запрос, определяющий коллекцию полей. Дополнительные сведения см. в статье [Analysis Services DMX Query Designer User Interface](../../reporting-services/report-data/analysis-services-dmx-query-designer-user-interface.md).  
  
 Имя созданного набора данных появляется на панели «Данные отчета» в виде узла под соответствующим источником данных.  
  
 После публикации отчета может понадобиться изменить учетные данные источника данных, чтобы разрешения, необходимые для получения данных при запуске отчета на сервере отчетов, были допустимыми.  
  
### <a name="to-create-an-embedded-microsoft-sql-server-analysis-services-data-source"></a>Создание внедренного источника данных служб Microsoft SQL Server Analysis Services  
  
1.  На панели инструментов в области данных отчета нажмите кнопку **Создать**и выберите **Источник данных**.  
  
2.  В диалоговом окне **Свойства источника данных** в текстовое поле **Имя** введите имя или примите имя по умолчанию.  
  
3.  Убедитесь, что выбран параметр **Внедренное соединение** .  
  
4.  В раскрывающемся списке **Тип** выберите пункт **Службы Microsoft SQL Server Analysis Services**.  
  
5.  Укажите строку соединения, соответствующую источнику данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
     Данные для строки соединения и учетные данные для подключения к источнику данных можно получить у администратора базы данных. Ниже приведен пример строки соединения для образца базы данных [!INCLUDE[ssSampleDBDWobject](../../includes/sssampledbdwobject-md.md)] на локальном клиенте.  
  
    ```  
    Data Source=localhost;Initial Catalog=AdventureWorksDW2012  
    ```  
  
6.  Нажмите кнопку **Учетные данные**.  
  
     Введите учетные данные, используемые для соединения с источником данных. Дополнительные сведения см. в статье [Задание учетных данных и сведениях о соединении для источников данных отчета](../../reporting-services/report-data/specify-credential-and-connection-information-for-report-data-sources.md).  
  
    > [!NOTE]  
    >  Чтобы проверить соединение с источником данных, нажмите кнопку **Изменить**. В диалоговом окне **Свойства соединения** нажмите кнопку **Проверить соединение**. Если проверка прошла успешно, появится информационное сообщение: «Проверка соединения завершилась успешно». Если проверка не прошла, появится предупреждающее сообщение с дополнительной информацией о причинах ошибки.  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     Источник данных появится в области данных отчета.  
  
### <a name="to-create-a-dataset-for-a-microsoft-sql-server-analysis-services"></a>Создание набора данных для служб Microsoft SQL Server Analysis Services  
  
1.  В области **Данные отчета** щелкните правой кнопкой мыши имя источника данных, который соединяется с источником данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], и выберите **Добавить набор данных**.  
  
2.  В диалоговом окне **Свойства набора данных** введите имя в текстовое поле **Имя** .  
  
3.  В поле **Источник данных**убедитесь, что указанное имя является именем источника данных, соединяющегося со службами [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
4.  Нажмите кнопку **Конструктор запросов** , чтобы открыть графический конструктор запросов для интерактивного построения запроса. Если конструктор запросов откроется в режиме многомерных выражений (MDX), нажмите на панели инструментов кнопку **Расширения интеллектуального анализа данных командного типа** (![Переключение в режим DMX-запросов](../../reporting-services/report-data/media/rsqdicon-commandtypedmx.gif "Переключение в режим языка DMX-запросов")), чтобы переключиться на конструктор запросов интеллектуального анализа данных. Дополнительные сведения см. в статье [Analysis Services DMX Query Designer User Interface](../../reporting-services/report-data/analysis-services-dmx-query-designer-user-interface.md).  
  
     Либо, чтобы импортировать существующий запрос расширений интеллектуального анализа данных из другого отчета, нажмите кнопку **Импорт**и перейдите к RDL-файлу, содержащему запрос. Импорт запросов из DMX-файлов не поддерживается.  
  
5.  Для просмотра образца результатов после создания и выполнения запроса нажмите **ОК**.  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     Набор данных и его коллекция полей появляются в области данных отчета под узлом источника данных.  
  
## <a name="see-also"></a>См. также:  
 [Тип соединения служб Analysis Services для расширений интеллектуального анализа данных (службы SSRS)](../../reporting-services/report-data/analysis-services-connection-type-for-dmx-ssrs.md)   
 [Создание строк подключения к данным (построитель отчетов и службы SSRS)](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)   
 [Коллекция полей набора данных (построитель отчетов и службы SSRS)](../../reporting-services/report-data/dataset-fields-collection-report-builder-and-ssrs.md)   
 [Внедренные и общие наборы данных отчета (построитель отчетов и службы SSRS)](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
  
