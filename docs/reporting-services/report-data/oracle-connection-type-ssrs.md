---
title: Тип соединения Oracle (службы SSRS, Сервер отчетов Power BI и построитель отчетов) | Документация Майкрософт
ms.date: 07/26/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-data
ms.topic: conceptual
ms.assetid: 9db86dd2-beda-42d8-8af7-2629d58a8e3d
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 2942ad1432b2674ab0b9906b5ab6e2f07be83ae7
ms.sourcegitcommit: a154b3050b6e1993f8c3165ff5011ff5fbd30a7e
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/30/2019
ms.locfileid: "68632074"
---
# <a name="oracle-connection-type-ssrs-power-bi-report-server-and-report-builder"></a>Тип соединения Oracle (службы SSRS, Сервер отчетов Power BI и построитель отчетов)

Чтобы использовать в отчете данные из базы данных Oracle, необходим набор данных, основанный на источнике данных Oracle. Этот встроенный тип источника данных напрямую использует поставщик .NET Framework для Oracle и требует наличия клиентского программного обеспечения Oracle. В этой статье объясняется, как скачать и установить драйверы для Reporting Services, Сервер отчетов Power BI и построитель отчетов.

## <a name="64-bit-drivers-for-the-report-servers"></a>64-разрядные драйверы для серверов отчетов

Сервер отчетов Power BI и SQL Server Reporting Services 2016 и 2017 используют управляемый ODP.NET. Следующие шаги необходимы только при использовании последних драйверов 18x. Предполагается, что вы установили файлы в c:\oracle64.

1. На сайте загрузки Oracle установите [oracle 64-разрядный универсальный УСТАНОВЩИК ODAC Oracle (OUI)](https://www.oracle.com/technetwork/topics/dotnet/downloads/odacdeploy-4242173.html). 
2. Регистрация управляемого клиента ODP.NET в глобальном кэше сборок: C:\oracle64\product\18.0.0\client_1\odp.net\bin\4\OraProvCfg.exe/Action: GAC/провидерпас: C:\oracle64\product\18.0.0\client_1\odp.net\managed\common\Oracle.ManagedDataAccess.dll
3. Добавьте записи управляемого клиента ODP.NET в файл Machine. config: C:\oracle64\product\18.0.0\client_1\odp.net\bin\4\OraProvCfg.exe/Action: config/Force/продукт: одпм/фрамеворкверсион: v 4.0.30319/ProductVersion: 4.122.18.3

## <a name="32-bit-drivers-for-report-builder"></a>32-разрядные драйверы для построитель отчетов
Следующие шаги необходимы только при использовании последних драйверов 18x. Предполагается, что вы установили файлы в c:\oracle32.

1. На сайте загрузки Oracle установите [oracle 32-разрядный универсальный УСТАНОВЩИК ODAC Oracle (OUI)](https://www.oracle.com/technetwork/topics/dotnet/downloads/odacdev-4242174.html).
2. Регистрация управляемого клиента ODP.NET в глобальном кэше сборок: C:\oracle32\product\18.0.0\client_1\odp.net\bin\4\OraProvCfg.exe/Action: GAC/провидерпас: C:\oracle32\product\18.0.0\client_1\odp.net\managed\common\Oracle.ManagedDataAccess.dll
3. Добавьте записи управляемого клиента ODP.NET в файл Machine. config: C:\oracle32\product\18.0.0\client_1\odp.net\bin\4\OraProvCfg.exe/Action: config/Force/продукт: одпм/фрамеворкверсион: v 4.0.30319/ProductVersion: 4.122.18.3

 Используйте сведения в этом разделе для создания источника данных. Пошаговые инструкции см. в разделе [Добавление и проверка подключения к данным (построитель отчетов и службы SSRS)](../../reporting-services/report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md).  
  
##  <a name="Connection"></a> Строка подключения  
 Данные для строки соединения и учетные данные для подключения к источнику данных можно получить у администратора базы данных. В следующем примере строки соединения указывается база данных Oracle на сервере Oracle18 с использованием Юникода. Имя сервера должно соответствовать значению, определенному в файле конфигурации tnsnames.ora в качестве имени экземпляра сервера Oracle.  
  
```  
Data Source="Oracle"; Unicode="True"  
```  
  
 Дополнительные примеры строк соединения см. в разделе [Подключения к данным, источники данных и строки подключения в построителе отчетов](data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md).  
  
##  <a name="Credentials"></a> Учетные данные  
 Учетные данные необходимы для запуска запросов, локального предварительного просмотра отчетов, а также для предварительного просмотра отчетов на сервере отчетов.  
  
 После публикации отчета может понадобиться изменить учетные данные источника данных, чтобы разрешения, необходимые для получения данных при запуске отчета на сервере отчетов, были допустимыми.  
  
 Дополнительные сведения см. в статье [Задание учетных данных и сведениях о соединении для источников данных отчета](specify-credential-and-connection-information-for-report-data-sources.md).  
  
  
##  <a name="Query"></a> Запросы  
 Для создания набора данных можно выбрать хранимую процедуру из раскрывающегося списка или создать SQL-запрос. Чтобы построить запрос, воспользуйтесь текстовым конструктором запросов. Дополнительные сведения см. в разделе [Пользовательский интерфейс текстового конструктора запросов (построитель отчетов)](../../reporting-services/report-data/text-based-query-designer-user-interface-report-builder.md).  
  
 Можно указать хранимые процедуры, возвращающие только один результирующий набор. Использование курсорных запросов не поддерживается.  
  
##  <a name="Parameters"></a> Параметры  
 Если запрос включает переменные запроса, то автоматически создаются соответствующие параметры отчета. Этот модуль поддерживает именованные параметры. Oracle версии 9 или более поздней поддерживает параметры с несколькими значениями.  
  
 Параметры отчета создаются со значениями свойств по умолчанию, которые, возможно, потребуется изменить. Например, все параметры отчета имеют тип данных **Text**. После создания параметров отчета можно изменить значения по умолчанию. Дополнительные сведения см. в разделе [Параметры отчета (построитель отчетов и конструктор отчетов)](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md).  
  
  
##  <a name="Remarks"></a> Замечания  
 Прежде чем подключиться к источнику данных Oracle, системный администратор должен установить версию поставщика данных .NET для Oracle, поддерживающую получение данных из базы данных Oracle. Этот поставщик данных должен быть установлен на компьютере, где работает построитель отчетов, а также на сервере отчетов.  
  
 Дополнительные сведения см. в следующих разделах:  
  
-   [Как использовать службы Reporting Services для настройки и доступа к источнику данных Oracle](https://support.microsoft.com/kb/834305)  
-   [Как добавить разрешения для субъекта безопасности NETWORK SERVICE](https://support.microsoft.com/kb/870668)  
  
### <a name="alternate-data-extensions"></a>Альтернативные модули обработки данных 
 
 Также данные из базы данных Oracle можно получить с помощью источника данных OLE DB. Дополнительные сведения см. в разделе [Тип соединения OLE DB (службы SSRS)](../../reporting-services/report-data/ole-db-connection-type-ssrs.md).  

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions" 
### <a name="report-models"></a>Модели отчетов  

 Также можно создавать модели на основе базы данных Oracle.  
::: moniker-end
   
### <a name="platform-and-version-information"></a>Сведения о платформе и версии  

 Дополнительные сведения о поддержке платформ и версий см. в статье [Источники данных, поддерживаемые службами Reporting Services (SSRS)](../../reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs.md).  

  
## <a name="see-also"></a>См. также:

 [Параметры отчета (построитель отчетов и конструктор отчетов)](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md)   
 [Фильтрация, группирование и сортировка данных (построитель отчетов и службы SSRS)](../../reporting-services/report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)   
 [Выражения (построитель отчетов и службы SSRS)](../../reporting-services/report-design/expressions-report-builder-and-ssrs.md)  
  
  
