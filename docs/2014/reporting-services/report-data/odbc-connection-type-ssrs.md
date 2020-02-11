---
title: Тип подключения к ODBC (службы SSRS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 24163866-f37a-4c38-982e-c3d79bf64d4c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 58c6a7aeca7bd465b793b7fa81fc56d15c27f060
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66107232"
---
# <a name="odbc-connection-type-ssrs"></a>Тип соединения ODBC (службы SSRS)
  Для включения данных из источника данных ODBC необходим набор данных на основе источника данных отчета типа ODBC. Этот встроенный тип источника данных основан на [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] модуле обработки данных ODBC.  
  
 Используйте сведения в этом разделе для создания источника данных. Пошаговые инструкции см. в статьях [Добавление и проверка подключения к данным или источника данных &#40;построитель отчетов и служб SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md).  
  
##  <a name="Connection"></a>Строка подключения  
 Строка соединения для модуля обработки данных ODBC зависит от требуемого драйвера ODBC. Обычная строка соединения содержит пары «имя-значение», поддерживаемые драйвером. Например, приведенная ниже строка соединения задает драйвер ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и базы данных AdventureWorks:  
  
```  
Driver={SQL Server Native Client 10.0};Server=server;Database=AdventureWorks;Trusted_Connection=yes;  
```  
  
  
##  <a name="Credentials"></a>Информации  
 Учетные данные необходимы для запуска запросов, локального предварительного просмотра отчетов, а также для предварительного просмотра отчетов на сервере отчетов.  
  
 После публикации отчета может понадобиться изменить учетные данные источника данных, чтобы разрешения, необходимые для получения данных при запуске отчета на сервере отчетов, были допустимыми.  
  
 Если источник данных ODBC настроен таким образом, что предлагается ввести пароль, либо пароль включен в строку соединения и пользователь вводит пароль, содержащий специальные символы (например, знаки препинания), драйверы некоторых базовых источников данных не смогут проверить специальные символы. Признаком этой ошибки может быть сообщение «Неверный пароль», появляющиеся при обработке отчета. Если изменение пароля невозможно, обратитесь к администратору базы данных, чтобы сохранить соответствующие учетные данные на сервере отчетов как часть системного имени источника данных ODBC (DSN). Дополнительные сведения см. в разделе «OdbcConnection.ConnectionString» документации по пакету SDK платформы [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] .  
  
> [!NOTE]  
>  Не рекомендуется включать в строку соединения такие сведения, относящиеся к имени входа, как пароли. В построителе отчетов в диалоговом окне **Источник данных** предусмотрена отдельная вкладка, где можно ввести учетные данные.  
  
 Дополнительные сведения см. в разделе [подключения к данным, источники данных и строки подключения в Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) или [укажите учетные данные в построитель отчетов](../specify-credentials-in-report-builder.md).  
  
  
##  <a name="Remarks"></a> Замечания  
 ODBC — технология доступа к данным, которая использовалась до появления OLEDB. ODBC поддерживает только реляционные источники данных. Поставщики данных ODBC называются *драйверами*. Драйверы ODBC поставляются корпорацией Майкрософт и сторонними производителями. Например, пакет Microsoft Office устанавливает драйверы ODBC, способные подключаться к файлам форматов Office.  
  
 Прежде чем можно будет создать строку соединения ODBC, необходимо сначала установить драйверы ODBC и задать DSN компьютера или системный DSN. Для успешного получения требуемых данных необходимо, чтобы синтаксис запроса поддерживался драйвером. Поддержка параметров различается в зависимости от конкретного драйвера. Дополнительные сведения см. в разделах по конкретным выбранным драйверам, например [SQL Server Native Client (ODBC)](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md).  
  
###### <a name="platform-and-version-information"></a>Сведения о платформе и версии  
 Дополнительные сведения о конкретных поставщиках данных ODBC данных см. в разделе [Источники данных, поддерживаемые службами Reporting Services (SSRS)](../create-deploy-and-manage-mobile-and-paginated-reports.md) документации по службам [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в электронной документации[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [ по ](https://go.microsoft.com/fwlink/?linkid=121312).  
  
  
##  <a name="HowTo"></a> Инструкции  
 В этом разделе содержатся пошаговые инструкции по работе с подключениями к данным, источниками данных и наборами данных.  
  
 [Добавление и проверка подключения к данным или источника данных &#40;построитель отчетов и служб SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md)  
  
 [Создание общего набора данных или внедренного набора данных &#40;построитель отчетов и служб SSRS&#41;](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)  
  
 [Добавление фильтра в набор данных &#40;построитель отчетов и SSRS&#41;](add-a-filter-to-a-dataset-report-builder-and-ssrs.md)  
  
  
##  <a name="Related"></a>Связанные разделы  
 В этих разделах документации содержатся подробные сведения о данных отчетов, а также методические сведения об определении, настройке и использовании элементов отчетов, связанных с данными.  
  
 [Добавление данных в построитель отчетов &#40;отчетов и SSRS&#41;](report-datasets-ssrs.md)  
 Предоставляет общие сведения о доступе к данным отчета.  
  
 [Подключения к данным, источники данных и строки подключения в построителе отчетов](../data-connections-data-sources-and-connection-strings-in-report-builder.md)  
 Предоставляет сведения о подключениях к данным и источникам данных.  
  
 [Внедренные и общие наборы данных отчета (построитель отчетов и службы SSRS)](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
 Предоставляет сведения об общих и внедренных наборах данных.  
  
 [Коллекция полей набора данных (построитель отчетов и службы SSRS)](dataset-fields-collection-report-builder-and-ssrs.md)  
 Предоставляет сведения о коллекции полей набора данных, создаваемой запросом.  
  
 [Источники данных, поддерживаемые Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) в [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] документации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [электронной документации](https://go.microsoft.com/fwlink/?linkid=121312)по.  
 Предоставляет подробные сведения о поддержке платформ и версий для каждого модуля обработки данных.  
  
  
## <a name="see-also"></a>См. также:  
 [Параметры отчета (построитель отчетов и конструктор отчетов)](../report-design/report-parameters-report-builder-and-report-designer.md)   
 [Фильтрация, группирование и сортировка данных (построитель отчетов и службы SSRS)](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)   
 [Выражения (построитель отчетов и службы SSRS)](../report-design/expressions-report-builder-and-ssrs.md)  
  
  
