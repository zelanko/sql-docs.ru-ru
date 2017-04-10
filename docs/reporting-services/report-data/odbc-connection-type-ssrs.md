---
title: "Тип соединения ODBC (службы SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 24163866-f37a-4c38-982e-c3d79bf64d4c
caps.latest.revision: 8
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 7
---
# Тип соединения ODBC (службы SSRS)
  Для включения данных из источника данных ODBC необходим набор данных на основе источника данных отчета типа ODBC. Этот встроенный тип источника данных основан на модуле обработки данных ODBC служб [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
 Используйте сведения в этом разделе для создания источника данных. Пошаговые инструкции см. в разделе [Добавление и проверка подключения к данным (построитель отчетов и службы SSRS)](../../reporting-services/report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md).  
  
##  <a name="Connection"></a> Строка подключения  
 Строка соединения для модуля обработки данных ODBC зависит от требуемого драйвера ODBC. Обычная строка соединения содержит пары «имя-значение», поддерживаемые драйвером. Например, приведенная ниже строка соединения задает драйвер ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и базы данных AdventureWorks:  
  
```  
Driver={SQL Server Native Client 10.0};Server=server;Database=AdventureWorks;Trusted_Connection=yes;  
```  
  
 ![Значок стрелки, используемый со ссылкой «В начало»](../../analysis-services/instances/media/uparrow16x16.png "Значок стрелки, используемый со ссылкой «В начало»") [В начало](#BackToTop)  
  
##  <a name="Credentials"></a> Учетные данные  
 Учетные данные необходимы для запуска запросов, локального предварительного просмотра отчетов, а также для предварительного просмотра отчетов на сервере отчетов.  
  
 После публикации отчета может понадобиться изменить учетные данные источника данных, чтобы разрешения, необходимые для получения данных при запуске отчета на сервере отчетов, были допустимыми.  
  
 Если источник данных ODBC настроен таким образом, что предлагается ввести пароль, либо пароль включен в строку соединения и пользователь вводит пароль, содержащий специальные символы (например, знаки препинания), драйверы некоторых базовых источников данных не смогут проверить специальные символы. Признаком этой ошибки может быть сообщение «Неверный пароль», появляющиеся при обработке отчета. Если изменение пароля невозможно, обратитесь к администратору базы данных, чтобы сохранить соответствующие учетные данные на сервере отчетов как часть системного имени источника данных ODBC (DSN). Дополнительные сведения см. в разделе «OdbcConnection.ConnectionString» документации по пакету SDK платформы [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] .  
  
> [!NOTE]  
>  Не рекомендуется включать в строку соединения такие сведения, относящиеся к имени входа, как пароли. В построителе отчетов в диалоговом окне **Источник данных** предусмотрена отдельная вкладка, где можно ввести учетные данные.  
  
 Дополнительные сведения см. в разделах [Подключения к данным, источники данных и строки подключения (построитель отчетов и службы SSRS)](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md) и [Указание учетных данных в построителе отчетов](../Topic/Specify%20Credentials%20in%20Report%20Builder.md).  
  
 ![Значок стрелки, используемый со ссылкой «В начало»](../../analysis-services/instances/media/uparrow16x16.png "Значок стрелки, используемый со ссылкой «В начало»") [В начало](#BackToTop)  
  
##  <a name="Remarks"></a> Замечания  
 ODBC — технология доступа к данным, которая использовалась до появления OLEDB. ODBC поддерживает только реляционные источники данных. Поставщики данных ODBC называются *драйверами*. Драйверы ODBC поставляются корпорацией Майкрософт и сторонними производителями. Например, пакет Microsoft Office устанавливает драйверы ODBC, способные подключаться к файлам форматов Office.  
  
 Прежде чем можно будет создать строку соединения ODBC, необходимо сначала установить драйверы ODBC и задать DSN компьютера или системный DSN. Для успешного получения требуемых данных необходимо, чтобы синтаксис запроса поддерживался драйвером. Поддержка параметров различается в зависимости от конкретного драйвера. Дополнительные сведения см. в разделах по конкретным выбранным драйверам, например [Собственный клиент SQL Server (ODBC)](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md).  
  
###### Сведения о платформе и версии  
 Дополнительные сведения о конкретных поставщиках данных ODBC данных см. в разделе [Источники данных, поддерживаемые службами Reporting Services (SSRS)](../../reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs.md) документации по службам [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в [электронной документации](http://go.microsoft.com/fwlink/?linkid=121312) по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Значок стрелки, используемый со ссылкой «В начало»](../../analysis-services/instances/media/uparrow16x16.png "Значок стрелки, используемый со ссылкой «В начало»") [В начало](#BackToTop)  
  
##  <a name="HowTo"></a> Инструкции  
 В этом разделе содержатся пошаговые инструкции по работе с подключениями к данным, источниками данных и наборами данных.  
  
 [Добавление и проверка подключения к данным (построитель отчетов и службы SSRS)](../../reporting-services/report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md)  
  
 [Создание общего или внедренного набора данных (построитель отчетов и службы SSRS)](../../reporting-services/report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)  
  
 [Добавление фильтра к набору данных (построитель отчетов и службы SSRS)](../../reporting-services/report-data/add-a-filter-to-a-dataset-report-builder-and-ssrs.md)  
  
 ![Значок стрелки, используемый со ссылкой «В начало»](../../analysis-services/instances/media/uparrow16x16.png "Значок стрелки, используемый со ссылкой «В начало»") [В начало](#BackToTop)  
  
##  <a name="Related"></a> См. также  
 В этих разделах документации содержатся подробные сведения о данных отчетов, а также методические сведения об определении, настройке и использовании элементов отчетов, связанных с данными.  
  
 [Наборы данных отчетов (службы SSRS)](../../reporting-services/report-data/report-datasets-ssrs.md)  
 Предоставляет общие сведения о доступе к данным отчета.  
  
 [Подключения к данным, источники данных и строки подключения в построителе отчетов](../Topic/Data%20Connections,%20Data%20Sources,%20and%20Connection%20Strings%20in%20Report%20Builder.md)  
 Предоставляет сведения о подключениях к данным и источникам данных.  
  
 [Внедренные и общие наборы данных отчета (построитель отчетов и службы SSRS)](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
 Предоставляет сведения об общих и внедренных наборах данных.  
  
 [Коллекция полей набора данных (построитель отчетов и службы SSRS)](../../reporting-services/report-data/dataset-fields-collection-report-builder-and-ssrs.md)  
 Предоставляет сведения о коллекции полей набора данных, создаваемой запросом.  
  
 [Источники данных, поддерживаемые службами Reporting Services (SSRS)](../../reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs.md), см. в документации к [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в [электронной документации](http://go.microsoft.com/fwlink/?linkid=121312) по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
 Предоставляет подробные сведения о поддержке платформ и версий для каждого модуля обработки данных.  
  
 ![Значок стрелки, используемый со ссылкой «В начало»](../../analysis-services/instances/media/uparrow16x16.png "Значок стрелки, используемый со ссылкой «В начало»") [В начало](#BackToTop)  
  
## См. также раздел  
 [Параметры отчета (построитель отчетов и конструктор отчетов)](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md)   
 [Фильтрация, группирование и сортировка данных (построитель отчетов и службы SSRS)](../../reporting-services/report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)   
 [Выражения (построитель отчетов и службы SSRS)](../../reporting-services/report-design/expressions-report-builder-and-ssrs.md)  
  
  