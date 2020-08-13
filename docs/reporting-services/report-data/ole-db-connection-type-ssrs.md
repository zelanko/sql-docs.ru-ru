---
title: Тип соединения OLE DB | Документация Майкрософт
description: В этой статье о типе подключения OLE DB вы узнаете, как создать источник данных.
ms.date: 03/17/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-data
ms.topic: conceptual
ms.assetid: d00cb13b-e1c2-4300-a195-3da1430a2df1
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 554622ce583bb314609c9000b1398ffbca4b6718
ms.sourcegitcommit: 9470c4d1fc8d2d9d08525c4f811282999d765e6e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2020
ms.locfileid: "86458229"
---
# <a name="ole-db-connection-type-ssrs"></a>Тип соединения OLE DB (службы SSRS)
  Для включения данных из источника данных OLE DB необходим набор данных на основе источника данных отчета типа OLE DB. В основе этого встроенного типа источника данных лежит модуль обработки данных OLE DB [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
 OLE DB представляет собой технологию доступа к данным, позволяющую клиентам подключаться к различным поставщикам данных. После выбора источника данных OLE DB необходимо выбрать определенный поставщик данных. Поддержка различных функций, таких как параметры и учетные данные, зависит от выбранного поставщика данных.  
  
 Используйте сведения в этом разделе для создания источника данных. Пошаговые инструкции см. в разделе [Добавление и проверка подключения к данным (построитель отчетов и службы SSRS)](../../reporting-services/report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md).  
  
##  <a name="connection-string"></a><a name="Connection"></a> Строка подключения  
 Строка соединения для модуля обработки данных OLE DB зависит от требуемого поставщика данных. Обычная строка соединения содержит пары имя-значение, поддерживаемые поставщиком данных. Например, приведенная ниже строка соединения задает поставщика OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и базы данных AdventureWorks:  
  
```  
Provider=SQLNCLI10.1;Data Source=server; Initial Catalog=AdventureWorks  
```  
  
 Используемая строка подключения зависит от внешнего источника данных, с которым выполняется соединение. Чтобы установить свойства строки соединения для поставщика данных, на странице **Общие** диалогового окна **Свойства источника данных** нажмите кнопку **Построить** , чтобы открыть диалоговое окно **Свойства соединения** . Расширенные свойства источника данных задаются в диалоговом окне **Свойства связи данных** .  
  
 См. примеры строк подключения в руководстве по [созданию строк подключения к данным (построитель отчетов и SSRS)](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md).  
  
  
##  <a name="credentials"></a><a name="Credentials"></a> Учетные данные  
 Учетные данные необходимы для запуска запросов, локального предварительного просмотра отчетов, а также для предварительного просмотра отчетов на сервере отчетов.  
  
 После публикации отчета может понадобиться изменить учетные данные источника данных, чтобы разрешения, необходимые для получения данных при запуске отчета на сервере отчетов, были допустимыми.  
  
 Дополнительные сведения см. в статье [Задание учетных данных и сведениях о соединении для источников данных отчета](specify-credential-and-connection-information-for-report-data-sources.md).  
  
###### <a name="special-characters-in-a-password"></a>Специальные символы в пароле  
 Если источник данных OLE DB настроен таким образом, что предлагается ввести пароль, либо пароль включен в строку подключения и пользователь вводит пароль, содержащий специальные символы (например, знаки препинания), драйверы некоторых базовых источников данных не смогут проверить специальные символы. При обработке отчета сообщение «Неверный пароль» может быть признаком этой ошибки.  
  
> [!NOTE]  
>  Не рекомендуется включать в строку соединения такие сведения, относящиеся к имени входа, как пароли. В построителе отчетов в диалоговом окне **Источник данных** предусмотрена отдельная вкладка, где можно ввести учетные данные.  
  
  
##  <a name="parameters"></a><a name="Parameters"></a> Параметры  
 Некоторые поставщики OLE DB поддерживают неименованные параметры и не поддерживают именованные параметры. Параметры передаются по расположению с помощью заполнителя в запросе. Символ заполнителя определяется синтаксисом, который поддерживается поставщиком данных.  
  
  
##  <a name="remarks"></a><a name="Remarks"></a> Замечания  
 OLEDB представляет собой собственную технологию создания поставщиков данных для определенных источников данных. Технология OLEDB основана на COM-интерфейсах. Технология OLEDB была разработана после появления технологии ODBC, но раньше поставщиков данных ADO.NET. Поставщики данных OLEDB регистрируются в операционной системе аналогично остальным COM-компонентам. Поставщики данных OLEDB предоставляются корпорацией Майкрософт и сторонними производителями. Корпорация Майкрософт также предоставляет MSDASQL, поставщик данных OLEDB, обеспечивающий мост с драйверами ODBC. Дополнительные сведения см. в разделе [Тип подключения к ODBC (службы SSRS)](../../reporting-services/report-data/odbc-connection-type-ssrs.md).  
  
 Для успешного получения требуемых данных необходимо, чтобы синтаксис запроса поддерживался поставщиком данных. Поддержка параметров различается в зависимости от поставщика данных. Дополнительные сведения см. в разделах по выбранным поставщикам данных. Пример:  
  
-   [Поставщик OLE DB служб Analysis Services (службы Analysis Services — многомерные данные)](https://docs.microsoft.com/analysis-services/instances/data-providers-used-for-analysis-services-connections
)  
   
  
-   [SQL Server Native Client (OLE DB)](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
  
 Дополнительные сведения о конкретных поставщиках данных OLE DB см. в статье [Источники данных, поддерживаемые службами Reporting Services &#40;SSRS&#41;](../../reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs.md).  
  
  
##  <a name="how-to-topics"></a><a name="HowTo"></a> Инструкции  
 В этом разделе содержатся пошаговые инструкции по работе с подключениями к данным, источниками данных и наборами данных.  
  
 [Добавление и проверка подключения к данным (построитель отчетов и службы SSRS)](../../reporting-services/report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md)  
  
 [Создание общего или внедренного набора данных (построитель отчетов и службы SSRS)](../../reporting-services/report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)  
  
 [Добавление фильтра к набору данных (построитель отчетов и службы SSRS)](../../reporting-services/report-data/add-a-filter-to-a-dataset-report-builder-and-ssrs.md)  
  
  
##  <a name="related-sections"></a><a name="Related"></a> См. также  
 В этих разделах документации содержатся подробные сведения о данных отчетов, а также методические сведения об определении, настройке и использовании элементов отчетов, связанных с данными.  
  
 [Наборы данных отчетов (службы SSRS)](../../reporting-services/report-data/report-datasets-ssrs.md)  
 Предоставляет общие сведения о доступе к данным отчета.  
  
 [Создание строк подключения к данным (построитель отчетов и SSRS)](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)  
 Предоставляет сведения о подключениях к данным и источникам данных.  
  
 [Внедренные и общие наборы данных отчета (построитель отчетов и службы SSRS)](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
 Предоставляет сведения об общих и внедренных наборах данных.  
  
 [Коллекция полей набора данных (построитель отчетов и службы SSRS)](../../reporting-services/report-data/dataset-fields-collection-report-builder-and-ssrs.md)  
 Предоставляет сведения о коллекции полей набора данных, создаваемой запросом.  
  
 [Источники данных, поддерживаемые службами Reporting Services &#40;SSRS&#41;](../../reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs.md).  
 Предоставляет подробные сведения о поддержке платформ и версий для каждого модуля обработки данных.  
  
  
## <a name="see-also"></a>См. также:  
 [Параметры отчета (построитель отчетов и конструктор отчетов)](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md)   
 [Фильтрация, группирование и сортировка данных (построитель отчетов и службы SSRS)](../../reporting-services/report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)   
 [Выражения (построитель отчетов и службы SSRS)](../../reporting-services/report-design/expressions-report-builder-and-ssrs.md)  
  
  
